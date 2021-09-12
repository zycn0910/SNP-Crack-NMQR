# 牛马二维码—一劳永逸的少年派破解环境搭建

## 项目介绍

该项目通过第三方拦截抓包来实现少年派扫描通用二维码来进行恢复出厂设置，使用过程相对人机友好，简单易上手

## 配置要求

服务器2GB+运存，50GB+储存

## 环境搭建

1.安装宝塔面板（Windows，Linux，SSH）任意

2.宝塔网页端选择IIS套件（无脑一键安装）

3.左栏网站➡添加站点➡搭建网站，绑定设置为：`【你的服务器IP】:【端口号】`，其余默认

4.将所提供的文件夹解压至您的网站根目录

## 软件安装与配置

一.安装与配置CCproxy

1. 打开设置
2. 修改HTTP协议端口（区别于环境搭建3端口）
3. 打开高级
4. 选择二级代理设置
5. 勾选启用，代理指向：`127.0.0.1`端口号：`【自定义端口号】`（区别于HTTP协议端口和环境搭建3端口）

二.安装与配置Fiddler

1. 上方状态栏点击Tools➡Options
2. 弹出安装证书一路【是】安装
3. General页面五个选项全勾选，其他参数默认
4. HTTPS页面四个选项全勾选，其他参数默认
5. Connections页面除了Use PAC Script其余全部勾选，端口：`【自定义】`（注意区别与上文设置的端口）

## 使用方法

1. 打开Fiddler，选择AutjResponder➡Add rule
2. 上栏填写8位码所提供的指定url（必须全称，下同），下栏填写`http://【你的服务器IP】:【端口号】/qr/cattle/8.js`
3. 再次点击Add rule
4. 上栏填写9位码所提供的指定url，下栏填写`http://【你的服务器IP】:【端口号】/qr/horse/9.js`
5. 保存全部，重启Fiddler
6. 打开CCproxy，点击启动按钮
7. 打开平板设置➡WiFi设置➡长按所连接的WiFi➡修改网络配置➡代理服务器➡手动➡服务器地址：`【你的服务器IP】`端口号：`【CCproxy的HTTP协议端口】`其余默认，点击保存
8. 打开平板浏览器，访问任意网址，显示`【fiddler】`开头的英文提示，表示连接服务器成功
9. 打开少年派➡左上角三条杠➡登出➡左下角切换账号（重启）
10. 重启后在少年派wifi管理页面再次检查是否为修改过的WiFi
11. 扫描提供的对应版本的牛马二维码，提示你牛马选项，点击进入恢复出厂设置

## 拓展

如果你的版本是在5.2，您将用到本栏目所介绍的内容

1. 创建代理服务器的pac文件
2. 将pac文件指定至你的网站根目录，确保访问为`http://【你的服务器IP】:【端口号】/pac/【filename.pac】`
3. 修改WiFi代理服务器，选择自动配置，指向【步骤2】中的地址
4. 打开Fiddler➡Options➡HTTPS页面➡点击右上角Action➡选择第二个选项（Export Root Certificate to Desktop）
5. 将桌面上生成的cer证书安装到平板上
6. 开始【使用方法步骤7】

## 题外话

1. 因为本项目涉及太多，暂不公开项目源码
2. 版本辨别，只区分版本号前两位数字`【5.1.x.xxx】【5.2.x.xxxxx】`
3. 本项目为Charles_Z原创，转载请标明出处
4. 你所使用的本项目但不仅限于项目内的源码所造成的任何后果，皆由使用者本人承担
5. 项目最终解释权归本人所有，你使用即代表同意
