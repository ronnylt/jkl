**jkl** is a static site generator written in [Go](http://www.golang.org),
based on [Jekyll](https://github.com/mojombo/jekyll)

Notable similarities between jkl and Jekyll:

* Directory structure
* Use of Front-End YAML matter in Pages and Posts
* Availability of `site`, `content`, `page` and `posts` variables in templates
* Copies all static files into destination directory

Notable differences between jkl and Jekyll:

* Uses [Go templates](http://www.golang.orgpkg/text/template)
* Only supports Front-End YAML matter in markup files
* Only processes pages and posts with .html, .markdown or .md extension
* No plugin support

Additional features:

* Deploy to S3

--------------------------------------------------------------------------------

### Installation

In order to compile with `go build` you will first need to download
the following dependencies:

```
go get github.com/russross/blackfriday
go get launchpad.net/goyaml
go get launchpad.net/goamz/aws
go get launchpad.net/goamz/s3
```
Once you have compiled `jkl` you can install with the following command:

```sh
sudo install -t /usr/local/bin jkl
```

by Jekyll. The same will happen for any `.html` or `.markdown` file in your
site's root directory.

### Usage

```
Usage: jkl [OPTION]... [SOURCE]

      --source         changes the dir where Jekyll will look to transform files
      --destination    changes the dir where Jekyll will write files to
      --server         starts a server that will host your _site directory
      --server-port    changes the port that the Jekyll server will run on
      --s3             copies the _site directory to s3
  -v, --verbose        runs Jekyll with verbose output
  -h, --help           display this help and exit

Examples:
  jkl                  generates site from current working dir
  jkl --server         generates site and serves at localhost:4000
  jkl /path/to/site    generates site from source dir /path/to/site

```

### Deployment

In order to deploy to S3 you must include a `_jekyll_s3.yml` file in your
site's root directory that specifies your AWS key, secret and bucket:

```
s3_id: YOUR_AWS_S3_ACCESS_KEY_ID
s3_secret: YOUR_AWS_S3_SECRET_ACCESS_KEY
s3_bucket: your.blog.bucket.com
```

Run `jkl --s3`

### Documentation

See the official [Jekyll wiki](https://github.com/mojombo/jekyll/wiki)
... just remember that you are using Go templates instead of Liquid templates.

