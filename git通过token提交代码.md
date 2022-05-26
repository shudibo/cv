#  Git 通过 token 提交代码

## Token 的生成：

> 登录 github.com 后，右边自己的头像处：
>
> 个人头像->Setttings->Developer settings->Personal access tokens->Generate new token   点这里进入 设置token 

## 本地配置方法：

### 清空本地密码
git config --local credential.helper ""

``` perl
[sdb@myserver /mnt/e/Web Development/cv main]$ git config --local credential.helper ""
【清除本地的密码，下面才会出现提示输入用户名和密码。】
[sdb@myserver /mnt/e/Web Development/cv main]$ git push
Username for 'https://github.com': shudibo  【这时输入用户名】
Password for 'https://shudibo@github.com':  【这时输入生成的 token ，代替原来的密码。】
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 651 bytes | 130.00 KiB/s, done.
Total 4 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/shudibo/cv.git
   17f09a6..1eea0fd  main -> main
[sdb@myserver /mnt/e/Web Development/cv main]$
```

![image-20220526195033025](git通过token提交代码.assets/image-20220526195033025.png)

###  设置 token
修改服务的配置，配置文件在 .git/config

![image-20220526194816633](images/image-20220526194816633-16535657384911.png)

用 记事本 程序打开这个文件：

![image-20220526195915197](images/image-20220526195915197.png)



```shell
[remote "origin"]
       url = https://{用户名}:{生成的token}@github.com/username/java.git
       fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
       remote = origin
       merge = refs/heads/main
```

> 说明：修改url，{用户名} 设置为自己提交的用户名，{生成的token} 替换成 token