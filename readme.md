# Description of Application

# Local Installation

## Prereq's

* Node 6.9.5+
* NPM 3.10.10+


# Deployment

Add the Production Server to your git remotes

```
git remote add production ssh://root@104.236.61.243:/var/repos/books.git
```

Push Master to production.

```
git push production master
```

TEST the server.!!!

# Server Setup

Create a cloud based server on Digital Ocean. $5

Install Node Via NVM

```shell
curl https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
```

Setup Git Hook to receive files from local

```shell
mkdir -p /var/repos/books.git
cd /var/repos/books.git
git init --bare
```

Add a Hook for git

```
nano /var/repos/books.git/hooks/post-receive
```

Add content to Hook file

```bash
#!/bin/bash

GIT_WORK_TREE=/var/www/books.com git checkout -f
```

Make hook executable

```
chmod +x /var/repos/books.git/hooks/post-receive
```

Make folder for work tree

```
mkdir -p /var/www/books.com
```
