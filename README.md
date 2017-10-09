# Raspberry_pi_learn

## 系统下载

    下载树莓派操作系统（Raspbian 基于 debian 的 Raspberry Pi 官方操作系统，如果是当开发板使用，最建议使用此系统）

    进入官网https://www.raspberrypi.org/downloads/下载Raspbian系统（下载系统时推荐下载RASPBIAN JESSIE WITH PIXEL完整版，RASPBIAN JESSIE LITE简装版不带图形化界面），下载完成后，将压缩包解压，获得Raspbian镜像文件。

## 树莓派系统烧录

    下载烧录工具（链接：http://pan.baidu.com/s/1bpA9TUZ 密码：nnzy）
    下载树莓派资料解压后，打开SD卡格式化工具（SD Formatter 4.0），将SD卡插入读卡器，插在电脑USB上，然后不需修改任何参数点击更新，更新完成之后，打开烧录系统工具（Win32DiskImager），选择镜像文件路径，以及SD卡路径，然后点击Write即可，烧录完成后会提示烧录成功。

## 树莓派系统启动
    
    将烧录好的SD卡插入树莓派，插上网线和电源
    
## 链接树莓派
    由于刚烧好的系统无法链接到网络，因此需要通过网线登录树莓派，设置wifi后再进行无线链接
    
### 网线直连PC
    1、连线。
    树莓派接好供电线；
    将网线一端接到树莓派，另一端接到笔记本。

    2、共享互联网。
    如果现在笔记本已经通过WIFI连接到互联网，可以将无线网卡的互联网资源共享给本地连接。以win7系统为例，开始——控制面板——网络和Internet——网络和共享中心——查看网络状态和任务——更改适配器设置，找到无线网络连接右键“属性”，在共享选项卡上选中“允许其他网络用户通过此计算机的Internet连接来连接（N）”选项，家庭网络链接中选“本地连接”，点确定。
    
    3、查找树莓派的IP地址。
    运行DOS窗口，输入arp -a，在接口192.168.137.1下的为动态类型的IP地址就是树莓派的地址
    
    为什么是接口192.168.137.1的呢？因为上部共享互联网的时候已把“本地连接”的IP地址自动设置成静态IP192.168.137.1了，当然这个IP地址也可以自己设置成其他自己常用的静态IP地址。因为此时树莓派的IP地址是动态的，只能用此方法查找。也可以通过修改SD卡中的cmdline.txt文件（在里面加入语句ip=***.***.***.***），将树莓派设置成静态IP地址，但此时只有将电脑的“本地连接”的静态IP地址设置成与树莓派静态IP地址同一号段才能成功连接。

### 利用PuTTY软件连接树莓派
    
    打开putty，填入树莓派的IP地址，然后回车，然后填入用户名：pi，密码：raspberry（密码输入时不会显示出来，不要误以为未输入），登陆成功即可进入系统。

#### ssh连接失败
    将全新的树莓派系统烧录，开机然后用SSH远程连接，结果SSH连接提示“connection refused”，导致连接树莓派失败。出现错误的原因是自 2016-11-25 官方发布的 Raspbian 系统镜像，系统默认禁用了 SSH 服务。

As of the November 2016 release, Raspbian has the SSH server disabled by default.

出错的详细信息为：

ssh: connect to host 192.168.43.220 port 22: Connection refused

官方的解决方案是：

    SSH disabled by default; can be enabled by creating a file with name "ssh" in boot partition

    如果有显示器，开机后，在树莓派配置中将SSH开启即可。但在没有显示器，首次开机需要用SSH登陆的时候，就需要在系统烧录完毕后，进入到boot分区盘， 新建一个名为ssh的空白文件就行了。

完成后再将SD卡插回树莓派，就可以正常使用SSH了。

### 修改网络配置


### 图形化界面连接。
    按照VNC远程登录树莓派的图形界面“http://shumeipai.nxez.com/2013/10/15/raspberry-pi-and-a-network-cable-directly-connected-laptop.html”一文就能通过VNC软件连接上树莓派进行图形化界面操作了，也可以通过windows自带的“远程桌面连接”功能进行图形化操作，具体设置可在网上查找相关教程。
    
    
    
