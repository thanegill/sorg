你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
# sorg [![Build Status](https://travis-ci.org/brandur/sorg.svg?branch=master)](https://travis-ci.org/brandur/sorg)

A Go-based build script that compiles my [personal website][brandur]. This is
the site's second incarnation, with the original being [a Ruby/Sintra
stack][org] (sorg = "static org").

The site deploys automatically from its CI build in Travis as changes are
committed to the master branch.

## Build

Install Go 1.9+, set up and run [blackswan][blackswan], then:

``` sh
go get -u github.com/ddollar/forego

cp .env.sample .env

# Used to run the test suite.
createdb sorg-test

# Compile Go executables.
make install

# Run an initial build of the site, look for build output in public/.
forego run make build

# Watch for changes in Go files and/or content and recompile and rebuild when
# one occurs.
forego start
```

The project can be deployed to s3 using:

``` sh
pip install awscli

export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
export S3_BUCKET=...
make deploy
```

## Development

Run the entire lifecycle like in CI:

``` sh
make
```

Run the test suite:

``` sh
make test
```

Run a single package's test suite or single test:

``` sh
go test ./markdown
go test ./markdown -run TestCollapseHTML
```

Get more verbose output while running tests:

```
go test -v ./markdown
```

## Vendoring Dependencies

Dependencies are managed with dep. New ones can be vendored
using these commands:

    dep ensure -add github.com/foo/bar

[blackswan]: https://github.com/brandur/blackswan
[brandur]: https://brandur.org
[org]: https://github.com/brandur/org
