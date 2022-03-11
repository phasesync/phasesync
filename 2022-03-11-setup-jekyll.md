---
layout: post
title: "Setup Github Pages (WSL2:Debian)"
date: 2022-03-11 09:55:11 +0100
categories: jekyll github pages
---
TL;DR for setting up a local Jekyll server

# Setup rbenv
[reference](https://github.com/rbenv/rbenv)
```
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

```text
export GEM_HOME=~/.gem
export GEM_PATH=~/.gem
export PATH="$PATH:$HOME/.rbenv/bin:$HOME/.gem/bin"
eval "$(rbenv init -)"
```

# Setup Ruby

```shell
$ gem update --system
$ rbenv install 2.7.3
$ rbenv global 2.7.3
$ rbenv local 2.7.3
$ rbenv rehash
$ ruby --version
$ gem --version

```

# Setup Git

```shell
mkdir webpage
cd webpage
git config --global init.defaultBranch main
git init
```

# Setup Jekyll

```shell
$ gem install jekyll
$ jekyll --version

$ gem uninstall jekyll
Select gem to uninstall:
 1. jekyll-3.9.0
 2. jekyll-4.2.2
 3. All versions
 
$ gem list jekyll
jekyll (4.2.2, 3.9.0)

$ rbenv rehash
```

Run a specific version of Jekyll. Github Pages works with Jeykyll [version](https://pages.github.com/versions/) 3.9.0.

```shell
$ jekyll _3.9.0_ -v
```

Create boilerplate.
```shell
$ jekyll _3.9.0_ new --skip-bundle .
```

Update Gemfile and choose the correct `github-pages` [version](https://pages.github.com/versions/).
```text
# gem "jekyll", "~> 3.9.0"
gem "github-pages", "~> 225", group: :jekyll_plugins
```

[reference](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)

```shell 
$ bundle install
```

Startup Jekyll web server.

```shell
$ bundle exec jekyll serve

...
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.

```
