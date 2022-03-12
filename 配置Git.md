Git 自带一个`git config`的工具来帮助设置控制 Git 外观和行为的配置变量。
这些变量存储在三个不同的位置:
1. `/etc/gitconfig`文件: 包含系统上每一个用户及他们仓库的通用配置。 如果在执行`git config`时带上`--system`选项，那么它就会读写该文件中的配置变量。(由于它是系统配置文件，因此你需要管理员或超级用户权限来修改它。) 
2. `~/.gitconfig`或`~/.config/git/config`文件:只针对当前用户。 你可以传递`--global`选项让 Git 读写此文件，这会对你系统上所有的仓库生效。
3.  当前使用仓库的 Git 目录中的`config`文件(即`.git/config`):针对该仓库。你可以传递`--local`选项让 Git 强制读写此文件，虽然默认情况下用的就是它。。 (当然，你需要进入某个 Git 仓库中才能让该选项生效。)
每一个级别会覆盖上一级别的配置，所以`.git/config`的配置变量会覆盖`/etc/gitconfig`中的配置变量。
使用Git，我们首先要设置用户名的邮箱和用户名
设置用户信息
```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
输入后进行检查: 
```bash
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
```
`--global`是对全局的设置，对系统上所有的仓库生效，进入某个项目更换为`--local`可以针对该仓库进行配置
#### 可选配置
文本编辑器的配置：
```bash 
$ git config --global core.editor vim //使用vim
```
缩写的配置：例如把status缩写为st，log --oneline --graph缩写为l，更改的设置也可以在~/.gitconfig中查看并修改
```bash
$ git config --global alias.st status
$ git config --global alias.l "log --oneline --graph"
```
