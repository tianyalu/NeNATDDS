# 内网穿透和会议室聊天

[TOC]

## 一、内网穿透理论

### 1.1 内网穿透

两台在不同局域网的设备不能直接通通讯，需要使用内网穿透技术来实现直接通讯。

内网穿透即`NAT(NetWork Address Translation)`穿透，实现方式为端口映射。

> 端口映射，其实就是常说的`NAT`地址转换的一种，其功能是把在公网的地址翻译成私有地址，采用路由方式的`ADSL`宽带路由器拥有一个动态或固定的公网`IP`，`ADSL`直接在`HUB`或交换机上，所有的电脑共享上网。
>
> 在局域网内部的任一`PC`或者服务器上运行到内网穿透客户端，此时域名解析到的`IP`地址是局域网网关出口处的公网`IP`地址，再在网关处做端口映射指向监控设备即可。

如下图所示：

![image](https://github.com/tianyalu/NeNATDDS/raw/master/show/nat_dds.png)

参考：[内网穿透技术](https://www.cnblogs.com/xingrui/p/10282288.html)

​			[NAT介绍](https://blog.csdn.net/ydfok/article/details/1467186)

​			[详细解读NAT和内网穿透](https://www.cnblogs.com/jiading/p/12029450.html)

### 1.2 音视频通话

音视频通话，顾名思义：双方能进行语音与视频之间的传输，要求低延时、降噪、高保真。目前实现音视频通话唯一的技术是`Webrtc`，包括微信、`QQ`、网易云、融云等都是基于`webrtc`展开的。

音视频通话实现过程：

* 音视频通话本质是通过`Socket`进行通信；
* 当连接建立好之后进行音视频内容传输；
* 最难的并不是音视频传输，而是网络建立的`p2p`连接。

## 二、会议室聊天

会议室聊天中音视频的部分是基于`webrtc`的`p2p`通信协议，而业务逻辑以及文本、图片以及文件等的传输是通过`socket`进程的：

![image](https://github.com/tianyalu/NeNATDDS/raw/master/show/meeting_room_chat.png)

