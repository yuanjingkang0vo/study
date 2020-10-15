***

# Github

***注：除`git init`  外其余git语句均只在自定义库中有效***

## 基础操作

`git init ` 将当前文件夹作为一个本地库。

`git add file`   将file文件加入仓库。

`git commit -m "注释"`  将缓存区的文件提交到本地库。

`git status`  查看当前仓库状态(主要查看本次同上次提交的差异)。

`git log`  查看最近提交版本及版本号。

* `git log --pretty=online`  简化最近版本显示。

`git reset --hard HEAD^`  回退到上个提交的版本。

* `git reset --hard HEAD^^`  回退到上两个版本。
* `git reset --hard 版本号` 回退到键入版本号版本。

`git relog`  查看更多的提交过版本号。

`git restore -- staged file`  同`git add file` 相反将file文件从仓库中移除。

`git checkout -- file`   撤销本次暂存区的所有操作。

`git checkout -b dev`  创建一个新的分支`dev`。

* `git checkout -b origin/dev` 创建远程`origin` 的`dev`分支到本地。

 `git branch`  查看当前存在的所有分支。

`git branch -d dev`  删除分支`dev`。

`git checkout dev`  切换到分支`dev`。

`git switch dev`  切换到分支`dev`。

`git merge dev` 合并分支。

`git switch -c dev`  创建新的分支`dev`并切换到新分支。

`git rm file ` and `git commit` 将文件`file`从版本库中删除。

`git remote add orign git@git.com:yuanjingkang0vo/file.git `  将本地库与已经存在的远程库关联起来。

`git push -u origin main` 将`main` 分支推送到远程库。在第一次推送时必须`-u` 。

`git pull` 将远程的最新提交抓取到本地。

`git branch -m oldname newname` 重命名本地分支。

> 后续应`git push --delete oldname` 删除远程分支 `git push -u origin newname` 将新命名的分支推到远程库。

`git clone git@github.com:yuanjingkang0vo/file.git` 克隆远程库到本地。

> 若仅克隆并不打算修改时`git clone git@github.com:目标仓库` 不必是自己的地址。若想要修改并上传到远程库则应首先`fork` 在远程库端将仓库克隆到自己的远程库中。再`git clone git@github:yuanjingkang0vo/仓库名` 。

`git branch --set-upstream-to=origin/dev dev` 将本地的`dev`分支与远程的`dev`分支链接起来。一般在`git pull`操作前应首先链接。

## 最新安装的github

```shell
$ git config --global user.name "Your name"
$ git config --global user.email "email@example.com"
```

这里设置全局仓库使用这个配置。

## ssh密钥

在本地推送到远程或是与远程库连接时一般要设置ssh密钥。

首先检查自己的电脑中是否有`.ssh`文件。若没有则

```shell
$ cd ~/.ssh
```

若存在则创建一个ssh key。

```shell
$ ssh-keygen -t -f rsa -C "your_email@example.com"
```

接下来全部回车跳过。不需要设置密码，若设置密码在每次进行`push`操作时都需要输入密码。

创建成功后，拷贝id_rsa.pub文件中的所有内容至github下。

```shell
$ clip < ~/.ssh/id_rsa.pub 
```

至此设置成功。