+++
title = "Getting started with Hugo"
author = ["penguwin"]
date = 2019-06-05
tags = ["blog", "go", "hugo"]
draft = false
+++

{{< figure src="/ox-hugo/hugo-logo-wide_2019-06-05_21-12-34.svg" >}}

[Hugo](https://gohugo.io) is an open source static site generator written in [Go](https://golang.org) which also claims
to be the fastest framework for building websites. With Hugo you can write
your posts in the [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) markup language and most configuration happens
inside a [toml](https://github.com/toml-lang/toml) file. It's simple to setup with just a couple of steps needed
and can be configured to match your wishes.
So let's give it a go :)


## Installation {#installation}

Hugo is commonly included by package managers - which I personally prefer
to use - but can also be installed via the repository.

Assumed you have a working [Go](https://golang.org) installation you can simply run following
commands and let the magic happen:

<a id="code-snippet--hugo-installation"></a>
```shell
go get -v -u github.com/gohugoio/hugo
cd $GOPATH/src/github.com/gohugoio/hugo
go install -v
```

After this Hugo should be installed on your system.

<a id="code-snippet--which-hugo"></a>
```shell
which hugo
```

```text
/home/penguwin/code/golang/bin/hugo
```

Now after we've installed the software we can start creating a new blog and
configure it's contents.


## Creating the blog {#creating-the-blog}

At first head into the folder where you locally want to store your blog
with it's files. There you can run following command to let hugo create a
sites skeleton with your desired name.

<a id="code-snippet--hugo-create-blog"></a>
```shell
hugo new site pengublog
```

Following message should be printed out after creation:

```text
Congratulations! Your new Hugo site is created in /home/penguwin/Nextcloud/projects/pengublog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

Now we have the basic structure for your site but we still need to tweak
it a little bit more. As we can see in the upper message we still need to
add a Theme and some content.


## Choosing a theme {#choosing-a-theme}

There's a wide variety of free and open source [themes](https://themes.gohugo.io) which can be used
for your blog. For this example I've choosen a clean and simple theme
called **finite** from the Hugo themes showcase.

Themes are added as git submodule. Head into your newly created folder and
hit following:

<a id="code-snippet--clone-theme"></a>
```shell
git init
git submodule add https://github.com/lambdafu/hugo-finite themes/finite
```

```text
Initialized empty Git repository in /home/penguwin/Nextcloud/projects/pengublog/.git/
```

You'll now be able to find the designs in the '/themes' folder. To
actually use it with Hugo you still need to declare it in your
**config.toml** file.

<a id="code-snippet--use-theme"></a>
```shell
echo 'theme = "finite"' >> config.toml
```


## Writing blog posts {#writing-blog-posts}

In order two have a nice blog, you need to add some content. With hugo
creating a post is also quite easy:

<a id="code-snippet--hugo-create-post"></a>
```shell
hugo new post/my-first-post.md
```

```text
/home/penguwin/Nextcloud/projects/pengublog/content/posts/my-first-post.md created
```

Now you can edit the markdown files content laying in `content/post/` as
you desire.


## Starting the hugo server {#starting-the-hugo-server}

Now we finally want to see our blog in action. To start the server with
drafts enabled you'll need following command:

<a id="code-snippet--starting-hugo-server"></a>
```shell
hugo server -D
```

If everything works out a message like this should be printed out.

```text
Building sites …
                   | EN
+------------------|-----+
  Pages            |   9
  Paginator pages  |   0
  Non-page files   |   0
  Static files     | 111
  Processed images |   0
  Aliases          |   1
  Sitemaps         |   1
  Cleaned          |   0

Total in 26 ms
Watching for changes in /home/penguwin/Nextcloud/projects/pengublog/{content,data,layouts,static,themes}
Watching for config changes in /home/penguwin/Nextcloud/projects/pengublog/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

As we can see the server waits at your [localhost](https://localhost:1313) and will live-reload as
soon as you edit the content of the blogs configs or markdown posts.


## Conclusion {#conclusion}

Getting started with Hugo is super easy and you can create a nice blog from
zero to ready-to-go in just a couple of commands.
There's still some work needed in order to publicate the blog into the wild
internet and of course we still have to personalize the blog with posts and
information about the author before we deploy it online.
For these further steps I can recommend reading the docs online as Hugo is
well documented and actively developed by a nice community.


## References {#references}

-   [Hugo Website](https://gohugo.io/)
-   [Quick Start](https://gohugo.io/getting-started/quick-start/)
-   [Documentation](https://gohugo.io/documentation/)
-   [Repository](https://github.com/gohugoio/hugo)
-   [Hugo Themes Collection](https://themes.gohugo.io/)


### Hugo help message {#hugo-help-message}

Here's the help text for hugo:

<a id="code-snippet--hugo-help-message"></a>
```shell
hugo version
hugo --help
```

```text
Hugo Static Site Generator v0.55.6/extended linux/amd64 BuildDate: unknown
hugo is the main command, used to build your Hugo site.

Hugo is a Fast and Flexible Static Site Generator
built with love by spf13 and friends in Go.

Complete documentation is available at http://gohugo.io/.

Usage:
  hugo [flags]
  hugo [command]

Available Commands:
  config      Print the site configuration
  convert     Convert your content to different formats
  env         Print Hugo version and environment info
  gen         A collection of several useful generators.
  help        Help about any command
  import      Import your site from others.
  list        Listing out various types of content
  new         Create new content for your site
  server      A high performance webserver
  version     Print the version number of Hugo

Flags:
  -b, --baseURL string         hostname (and path) to the root, e.g. http://spf13.com/
  -D, --buildDrafts            include content marked as draft
  -E, --buildExpired           include expired content
  -F, --buildFuture            include content with publishdate in the future
      --cacheDir string        filesystem path to cache directory. Defaults: $TMPDIR/hugo_cache/
      --cleanDestinationDir    remove files from destination not found in static directories
      --config string          config file (default is path/config.yaml|json|toml)
      --configDir string       config dir (default "config")
  -c, --contentDir string      filesystem path to content directory
      --debug                  debug output
  -d, --destination string     filesystem path to write files to
      --disableKinds strings   disable different kind of pages (home, RSS etc.)
      --enableGitInfo          add Git revision, date and author info to the pages
  -e, --environment string     build environment
      --forceSyncStatic        copy all files when static is changed.
      --gc                     enable to run some cleanup tasks (remove unused cache files) after the build
  -h, --help                   help for hugo
      --i18n-warnings          print missing translations
      --ignoreCache            ignores the cache directory
  -l, --layoutDir string       filesystem path to layout directory
      --log                    enable Logging
      --logFile string         log File path (if set, logging enabled automatically)
      --minify                 minify any supported output format (HTML, XML etc.)
      --noChmod                don't sync permission mode of files
      --noTimes                don't sync modification time of files
      --path-warnings          print warnings on duplicate target paths etc.
      --quiet                  build in quiet mode
      --renderToMemory         render to memory (only useful for benchmark testing)
  -s, --source string          filesystem path to read files relative from
      --templateMetrics        display metrics about template executions
      --templateMetricsHints   calculate some improvement hints when combined with --templateMetrics
  -t, --theme strings          themes to use (located in /themes/THEMENAME/)
      --themesDir string       filesystem path to themes directory
      --trace file             write trace to file (not useful in general)
  -v, --verbose                verbose output
      --verboseLog             verbose logging
  -w, --watch                  watch filesystem for changes and recreate as needed

Additional help topics:
  hugo check   Contains some verification checks

Use "hugo [command] --help" for more information about a command.
```


### Hugo environment {#hugo-environment}

This is how my hugo environment looks like after installation:

<a id="code-snippet--hugo-environment"></a>
```shell
hugo env
```

```text
Hugo Static Site Generator v0.55.6/extended linux/amd64 BuildDate: unknown
GOOS="linux"
GOARCH="amd64"
GOVERSION="go1.12.4"
```
