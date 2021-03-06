git init命令把这个目录变成Git可以管理的仓库

git add filename 把文件添加到暂存区

git status 查看仓库状态

git diff filename 查看修改的内容

git commit -m "message" 把暂存区提交到仓库

git log 显示提交日志  加上--pretty=oneline 减少显示的信息

git reset --hard HEAD^ 返回上一个版本 (HEAD^^)代表上上版本，一次类推,或者用HEAD~100代表上100个版本

git reflog 显示每一次的命令，可以查到commit id

git reset --hard commit_id 返回该commit id 的版本

git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别

git checkout -- file可以丢弃工作区的修改，分两种情况：
1.readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态。
2.readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总结：回到最近的一次git commit或git add时的状态

git reset HEAD <file>可以把暂存区的修改撤销掉,重新放回工作区

删除文件：git rm删掉，并且git commit

git push origin与git push -u origin master的区别
$ git push origin

上面命令表示，将当前分支推送到origin主机的对应分支。 

如果当前分支只有一个追踪分支，那么主机名都可以省略。 

$ git push 如果当前分支与多个主机存在追踪关系，那么这个时候-u选项会指定一个默认主机，这样后面就可以不加任何参数使用git push。

$ git push -u origin master 上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。

不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。

要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git
	例如：$ git remote add origin git@github.com:xl695703025/learngit.git
	或者$git remote add origin https://github.com/xl695703025/learngit.git

$ git clone git@github.com:michaelliao/gitskills.git 将远程库克隆到本地
例如: $ git clone git@github.com:xl695703025/gitskills.git
或$git clone https://github.com/xl695703025/gitclone

注意:git支持多种协议，默认git://，也可以使用https等其他协议，但是使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。

总结：Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

$git checkout -b dev 创建新的分支dev，并且切换到dev
等同于：
$git branch dev 创建分支

$git checkout dev 切换分支

$git branch <name> 查看分支

$git merge <name> 合并分支,合并指定分支到当前分支。
--no-ff  该参数可以使用普通模式合并，通常情况是Fast forward模式。

$git branch -d <name>删除分支 -D强行删除

$git log --graph 合并分支图

$git stash 可以把当前工作现场“储藏”起来

$git stash list  查看储藏的内容

$git stash apply 恢复
$git stash drop 删除
$git stash pop 恢复并删除

多人协作的工作模式通常是这样：
1.首先，可以试图用git push origin <branch-name>推送自己的修改；
2.如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
3.如果合并有冲突，则解决冲突，并在本地提交；
4.没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！
5.如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。
这就是多人协作的工作模式，一旦熟悉了，就非常简单

查看远程库信息，使用$ git remote -v

$git tag <tagname>  打标签
$git tag <tagname> <commitid> 根据commitid打标签

$git show <tagname>查看标签信息

$ git tag -a v0.1 -m "version 0.1 released" 1094adb // -a指定标签名  -m指定说明文字

$git tag 查看所有标签

$ git tag -d <tagname>  删除标签

$git push orign <tagname> 推送tag

