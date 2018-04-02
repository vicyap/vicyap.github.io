---
layout: post
title:  "Building BKMRK"
date:   TODO
categories: software
---

# BKMRK

What is `BKMRK`? Well you can find out more here: <https://github.com/bkmrk/bkmrk>.

Right now I just want to jot down some notes about some of the challenges I have faced with building bkmrk.

## Building a Modern Web App (12F)

What does it mean to be a modern web app? Essentially a stateless application process. But if it is stateless,
what about...

* logs

Lol so my one of my first difficulties with building this app was that I could not use file logging. This is new to me.
Well then you might say, "Duh! if an application has file logs, that implies state." I guess I took file logging
for granted. You can read more about logging for the modern web app here <https://12factor.net/logs>.

* configs

Oh joy... configs. So as of my writing right now. I have not figured this one out.


* deployment / dev ops


## Tooling and Technology (and why)

My current toolbelt as a developer is as follows:

### Python

* flask

At first I wanted to do this in Rust cause I have been itching to build something with Rust for a while now. But
then I realized I would probably be a quarter of the way to where I am now if I did it in Rust. Not to to diss
Rust or anything (I am a big fan), but there would just be more to build from scratch. Though I do plan to rewrite
the API in Rust later on.

I started building this app with this tutorial. <https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world>.
This tutorial is excellent. I think it is a great place to start for anyone trying to learn Flask and/or Python in
general.

So why did I choose Flask anyways? Well I feel comfortable with Python, and like I was mentioning earlier, I
wanted to focus on building that application, not learning a new language or having to build pieces myself. Thanks
to the massive Python community and all of their packages, I can leverage that to get up and started quickly.

* pipenv

Okay so why pipenv? Well one reason is it is PyPA's official tool for managing python application dependencies.
If it is that official, it's probably worth considering and learning. And as we all know in software, there
is also a shiny new tool around the corner. Sometimes the tool is a distraction, but sometimes it could be the next
breakthrough in your workflow (like vim was for me).

Okay so why not stick to the good old `virtualenv-wrapper` and `workon venv` workflow? I will admit that learning my
way around pipenv was frustrating at first. I didn't understand if I was supposed to edit the Pipfile or not. I did
not know how to run things that I installed, like flask. 

But after the initial learning / innovation tax (coined by <https://www.youtube.com/watch?v=ta3S8CRN2TM>), I have
learned to love pipenv. I do not have to think about virtualenvs anymore, which means I can swith in and out of my
project without a second thought (no more `deactivate`). Running commands from the virtualenv couldn't be easier.
`pipenv run <args...>`

* pytest

I learned about `pytest-xdist` which is helpful for speeding up pytest.

### Deployment

* Travis CI

The go to, free, off-the-shelf, CI solution. If you have a public github repo, you should hook up Travis CI.

Continuous Integration is a well-known best practice. To do otherwise is to comdemn yourself to a world of hurt and
manual testing. No one deserves to be manually testing software.

* Habitat

Habitat is the relatively new package building and package running tool from Chef.

* Ansible (soon not to be)

At first I planned to use ansible for server setup. However procedural tasks and convergent state did not appeal
to me very much. I have also used Ansible for work and between working with BKMRK and working work, I have grown a
slight distrust towards ansible.

Convergent state is hard to understand.

* Terraform (soon to be)

I played with Terraform a little bit on a side project (my-git-lfs-server) and I think it will fit in with the other
tools. It supports digital ocean, which is the provider I am using right now. And it also supports aws, which might
come in handy later.

Perhaps most interesting is that is allows the usage of habitat as a provisioner. So I can provision my droplets with
the habitat artifacts that I build.

### Other

* coveralls

Coverage CI.

* code climate

Code quality CI.
