# ztAutoService

#### 项目介绍

* windows下的进程管理器，能注册为服务随windows开机启动。
* 本项目以vs2012建立
* 编译前需要在属性管理器中将Microsoft.Cpp.x64.user(或Microsoft.Cpp.Win32.user)中修改以下：(或者在每个项目属性中都修改一次)
* * 常规-输出目录：$(SolutionDir)..\out\$(Platform)_$(Configuration)\
* * 常规-中间目录：$(SolutionDir)..\out\Temp\$(ProjectName)\$(Platform)_$(Configuration)\
* * 链接1器-常规-附加库目录：$(OutDir);%(AdditionalLibraryDirectories)

#### 配置文件说明

* 在exe文件目录放置一个json配置文件，内容按如下格式
* [{
*	"path":"C:\\Windows\\System32\\notepad.exe",  //执行的程序路径
*	"args":"",  //执行程序的参数
*	"daemon":"yes",  //是否启用进程守护
*   "rstime":"15:30:00", //指定时间点会重启程序
*	"rsdur":300,   //运行经过多久会重启，单位秒
*	"exedir":1,  //指定程序执行的工作目录  0:守护进程的工作目录 1:进程文件所在的目录 2:自定义,使用usrdir来指定
*   "usrdir":""  //用户自定义的工作目录
* },{...}
* ...
* ]


#### 安装教程

* 需要使用管理员权限的控制台进行系统服务的安装与卸载
1. as -i 安装名为as的系统服务并启动，以as.json为配置文件
2. as -i xxx 安装名为xxx的系统服务并启动，以xxx.json为配置文件
3. as -u 停止并卸载系统服务as
4. as -u xxx 停止并卸载系统服务xxx
5. 直接启动 以用户进程方式执行程序，作为进程管理工具使用，以as.json为配置文件
6. as xxx(xxx不以-开头) 以用户进程方式执行程序，作为进程管理工具使用，以xxx.json为配置文件
