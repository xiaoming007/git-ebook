# git基础
### 查看用户名
git config user.name
### 查看邮箱
git config user.email
### 查看配置信息
git config --list
### 修改用户名
git config --global user.name "xxxx"
### 修改密码
git config --global user.password "xxxx"
### 修改邮箱
git config --global user.email "xxxx"
### 查看文件的状态
git status 
### 忽略文件提交
在.gitignore文件中设置，使用!符号，表示把这个文件除外
### 从版本库中移除文件
git add 是添加当commit后想要删除，使用git rm {filename}这样会把原始文件也删掉，如果想要保存原始文件使用git rm --cached {filename} 这样只会删掉仓库中的文件，而原始文件还在
### 修改仓库中文件的名字
使用 git mv 原文件名 新文件名字
### git日志
* git log 查看日志
* git log -p 提交的详细信息
* git log -p -1 最近一次提交的信息
* git log --oneline 查看简短信息  
* git log --oneline -p也可以看到详细信息  
* git log --name-only 查看一下都有那些文件发生变化  
* git log --name-status 查看文件具体的变化类型，比如修改或者新增等  
### 修改提交的描述信息命令
git commit --amend 也可以对新添加的内容进行追加  
### git文件操作
* 第一次的时候从add区域撤回，git rm --cached {file}
* 如果已经commit到仓库后，想要撤回修改，使用 git reset HEAD {file}
* 如果想将文件恢复到上一次提交时的内容使用 git checkout -- {file}  
### 为常用命令添加别名
在git 的.gitconfig配置文件中添加
```
[alias]
		a = add .
		c = commit 
		l = log 
		s = status 
```
### git 分支
* git branch 查看分支  
* git branch {分支名} 创建一个新的分支  
* git checkout {分支名} 切换到新的分支  
* git checkout -b {分支名} 创建分支并且切换到新的分支  
### 分支的合并
* 首先切换到主分支，然后执行命令 git merge {分支名}
* 删除分支 git branch -d {分支名}  
### 冲突的解决  
手动打开冲突的文件，手动修改
### 分支管理merged及分支强制删除  
* 查看已经合并的分支，首先切换到主分支，然后使用命令 git branch --merged  
* 查看未合并的分支，首先切换到主分支，然后使用命令 git branch --no--marged  
* 如果想要删除未经合并的分支，直接执行 git branch -d {分支名} 会删除失败，需要使用命令 git branch -D {分支名}  
### 标准的分支操作流 
* master分支干净稳定  
* develop分支是开发分支，后续的功能都是在这个分支上切出的分支，对master有一个保护作用  
### stash临时存储区
* 当你正在分支开发功能时，突然有事情，需要切换到其他分支，直接切分支是不允许的，可以使用git stash 将文件暂存起来，然后再切换分支  
* 处理完后，切换回当前分支，然后恢复暂存区，使用 git stash apply  
* 使用git stash list 命令查看暂存区列表
* 如果想删除暂存区中的任务，使用 git stash drop {列表上的条目名字}  
* 使用 git stash pop 会执行两步操作，先恢复暂存区内容，然后删掉暂存内容  
### 使用TAG标签声明项目阶段版本
git tag v1.0 使用git tag 查看标签列表  
### 打zip包
git archive master --prefix='xxxxx/' --forma=zip > xxxxx.zip  
### 查看所有文件命令
ls -a
### rebase 说明
当在master上切出一个分支开发功能，但是master也被其他人不停进行分支合并后，执行rebase可以，将分支的切出点设置为master当前的被提交后的点上，在进行合并，有一个好处是，如果合并的时候出现冲突，可以有分支的创建者去处理，而不是master分支的维护者去处理  
执行命令 git rebase master  
### git 与远程服务器建立链接
* git remote add origin git@github.com:xxxxxxxx  链接远程服务器  
* git remote -v 查看远程服务器  
### 查看远程分支命令
git branch -a 查看远程分支  
### 将本地分支提交到远程 
git push --set-upstream origin {分支名}
### 拉取远程分支到当前分支
git pull origin xxx:xxx  
### 删除远程分支
git push origin --delete {分支名}，结合删除本地分支命令 git branch d {分支名}

























