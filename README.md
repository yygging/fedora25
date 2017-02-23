# fedora25
install user guide


# 1、安装chrome：
su root
cd /etc/yum.repos.d/                   ////添加chrome源

wget  http://repo.fdzh.org/chrome/google-chrome-mirrors.repo        ///下载google-chrome.repo并保存

dnf install -y google-chrome-stable        ///安装Chrome



# 2、安装ss-qt5：
sudo dnf copr enable librehat/shadowsocks               ///使用dnf添加shadowsocks的Copr源

sudo dnf update
sudo dnf install shadowsocks-qt5                        ///使用dnf更新cache并安装



# 3、终端挂ss：
sudo yum install polipo                           ///安装

sudo vi /etc/polipo/config   

    socksParentProxy = "localhost:1080"
    socksProxyType = socks5                            ///设置ParentProxy为Shadowsocks端口



sudo service polipo stop
sudo service polipo start                             ///启动和关闭




curl ip.gs                                               ///测试本地IP
http_proxy=http://localhost:8123 curl ip.gs              ///测试翻墙IP


           
export http_proxy=http://localhost:8123              ///全局代理
unset http_proxy                                     ///关闭全局



# 4安装网易云:

http://dl-http.senorsen.com/pub/package/linux/rpm/



# 5安装输入法:


sudo yum install fcitx-pinyin sudo yum install fcitx-configtool sudo yum install im-chooser        ///安装fcitx

yum erase ibus                ///卸载原来旧的输入法ibus

alternatives --config xinputrc              ///配置输入法

vi /etc/profile                         ///添加
         export GTK_IM_MODULE=fcitx  
         export XMODIFIERS="@im=fcitx"  
         export QT_IM_MODULE=fcitx  

reboot

下载搜狗deb包,将data.tar.xz提取出来,打开终端

sudo tar Jxvf data.tar.xz -C /                         ///将这个包解压到根目录下，接下来

sudo mv /usr/lib/x86_64-linux-gnu/fcitx/fcitx-sogoupinyin.so /usr/lib64/fcitx/                
           ///将搜狗拼音插件移动到fedora发行版中的相应位置



# 6安装screenfetch

yum install screenfetch


# 7安装微信
解压linux-x64.tar.gz , 运行 ./electronic-wechat 


# 8安装deb包
yum install alien

alien -r XXXXX.deb



# 9安装bumblebee
 dnf -y --nogpgcheck install http://install.linux.ncsu.edu/pub/yum/itecs/public/bumblebee-nonfree/fedora25/noarch/bumblebee-nonfree-release-1.2-1.noarch.rpm

 dnf install bumblebee-nvidia bbswitch-dkms VirtualGL.x86_64 VirtualGL.i686 primus.x86_64 primus.i686 kernel-devel

 lspci | grep -i vga              ///show 显卡

 glxgears                      ///测试核显

 optirun glxgears              ///测试独显





















