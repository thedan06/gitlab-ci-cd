# GitLab CI/CD SetUp

Step by step instruction of how to setup GitLab CI/CD.

`Note: there are two servers both running CentOs7, configured in VirtualBox both with NAT Network Adaptor (for internet access) and Host-Only (for host to VM and VM to VM communication/ssh)`

* GitLab (runnig both GitLab and GitLab-Runner)
* WebServer (hosting a web app in Apache/HTTPD server)

## 1. GitLab Installation
* Install GitLab, checkout this: <a href="https://about.gitlab.com/install/#centos-7">GitLab Installation, using GitLab Omnibus package

## 2. GitLab-Runner installation and setup
* Install gitlab-runner, checkout this: <a href="https://docs.gitlab.com/runner/install/linux-manually.html#using-debrpm-package">Install GitLab Runner | Using deb/rpm package</a>

## 3. Enveroment SetUp
* Generate SSH Key in your GitLab Server and copy the corresponsing public key to the WebServer, checkout steps: <a href="https://gist.github.com/thedan06/f3cb42775fbf9adc4f0fe5ff840019d2">Generating a passphraseless SSH key and use it to SSH to your Linux Server(s)
* Generate SSH key in your WebServer and copy the corresponding public key and copy it to the GitLab GUI, checkout this: <a href="https://docs.gitlab.com/ee/ssh/#adding-an-ssh-key-to-your-gitlab-account">Adding an SSH key to your GitLab account

## 4. CI/CD SetUp (the real magic)
* Add .gitlab-ci.yml in the root of your project and add appropriety command to suite your need, checkout the sample file: <a href="https://gist.github.com/thedan06/6abfea860b09bd08dcb98a415b71c32c">Sample GitLab .gitlab-ci.yml</a>. This file trigger a pipeline when developer push changes to master branch, it contains instruct of how shoult GitLab-runner excute commands, i.e. run test then ssh from GitLab to WebServer and deploy changes automatically
