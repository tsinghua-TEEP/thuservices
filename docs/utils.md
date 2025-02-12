# 一些脚本和工具

## 选课冲突标记

你还在为抢课时满怀期待提交选课，却发现时间冲突而错失选课吗？
你还在一边记忆已选课时间，一边对照开课列表而感到缓慢吗？
这个脚本帮你忙！

这个脚本检测你已经选好的课，自动将候选课中有冲突时间的课标红，使得你浏览
百万课程时速度有如神助。当鼠标在在标红的时间上悬停时，会显示所有与其冲突的课程。

需要注意的是，现在未对半学期课做完全支持，也就是说可能出现假的时间冲突；
同时在开课信息以及选课查询界面无法工作，只在选课操作界面工作。

本脚本在 aux/TsinghuaCourseConflictMarker.user.js 中，需要使用油猴安装。

或者可以通过访问[这里](https://greasyfork.org/en/scripts/408340-tsinghuacourseconflictmarker)
来一键获得脚本。

现在已经增加 webvpn 支持。

感谢 [CircuitCoder](https://github.com/CircuitCoder) 提供的技术指导
感谢 [SharzyL](https://github.com/SharzyL) 的建议与 DEBUG

## INFO 网络学堂 Telegram 消息推送

参见 [thu-weblearn-tgbot](https://github.com/Konano/thu-weblearn-tgbot) 以及
[thu-info-forwarder](https://github.com/Konano/thu-info-forwarder)。

在 Telegram 上已经存在 THU INFO CHANNEL，由于是私有频道，需要通过[邮件](mailto:i@zenithal.me)
获取邀请链接。

## 全校洗衣机状态

还在为了抢洗衣机而努力吗，还在跑上跑下却发现一个洗衣机都没有而痛苦吗，这个服务
帮你侦测洗衣机状态，足不出户而一键掌握全校洗衣机的动向！

源码在 repo 的 aux 目录中，需要自行填写 mopenid 使用。此项需要在微信端抓包获取。

目前部署在 cf workers 上，地址为 [https://washer.thu.services](https://washer.thu.services)

要实现搜索，我们需要加上参数，目前接受三种参数，「s」，「j」与「p」。「s」即为搜索的
字符串，一般接受的字符串为「x号楼y层」，前面可以冠名紫荆或南区。举例来说

```
https://washer.thu.services/?s=2号楼2层
```

会返回「紫荆2」与「南区12、32」的洗衣机运行情况。在该参数缺省的情况下，返回的是
「紫荆2号楼」的洗衣机运行情况。

另外也可以使用多个「s」参数，来获取多个关键词的搜索结果，比如

```
https://washer.thu.services/?s=紫荆3号楼&s=紫荆公寓3号楼&s=紫金公寓3号楼
```

会返回所有紫荆 3 号楼的洗衣机运行情况（部分洗衣机的名称中有 typo）。

对于「j」参数，我们只检查「j」是否存在，若存在，则返回原始的 json 数据，
此项供开发者使用。「s」与「j」参数可同时使用。

对于「p」参数，我们只检查「p」是否存在，若存在，则返回 text/plain 数据，
「s」与「p」参数可同时使用。当「j」与「p」同时出现时，「j」的优先级更高。


### 全校洗衣机状态 - iOS 快捷方式

iOS 12 以上的用户可以透过此[链接](https://www.icloud.com/shortcuts/ffc9d9fff7e140ec9e5a92e5f7d16ae0)安装快捷方式以实现快速查询空闲洗衣机。目前仅支持精确度至楼层的查询。 

### 全校洗衣机状态 - Telegram Bot 二哈

基于该接口[Konano](https://github.com/Konano)开发了一个 Telegram Bot，名为二哈。

项目地址在[此](https://github.com/Konano/Tuna-Erha-Bot)，在洗衣机状态查询功能外，还有更多功能。

可以通过[t.me/erhabot](https://t.me/erhabot) 访问该 Bot。

### 洗衣监控与提醒 - 微信小程序

![THU洗衣](image/washer.jpg)

使用同一套API，在关注洗衣机后，当洗衣机空闲时，会通过微信服务号发送提醒。

[项目地址](https://github.com/zrt/thu-wash-notify)

## INFO GPA 计算器

在 cksqs 失败后难以一键查询 GPA 吗，抑或需要割肉花 10 元才能得到 GPA 吗，
这种只保留了 3 位有效数字的 GPA，由于 [-0.005,0.005) 的舍入，让人感到极大的不确定性；
而对于手算 GPA 的同学，由于学年的增加，课程的增多，手算的难度也越来越高，每出一门课
就需要算一次 GPA，负担极重。

于是，我们提出自动的 GPA 计算功能，考虑到方便、好用等各种因素，我们与往常一样，
推出 userscript 来实现这一小功能。

本脚本只会读取「INFO-全部成绩」界面中存在的成绩（已经录入系统但没发布的，只能
通过 cksqs 或付费成绩单获取的，不在计算范围内），用新、旧算法将全部 GPA 与必限 GPA
计算出来（直接输出 double），并弹出通知提醒。

本脚本在 `aux/Tsinghua GPA Calculator.user.js` 中，需要使用油猴安装。

或者通过[这里](https://greasyfork.org/zh-CN/scripts/410960-tsinghua-gpa-calculator)
来获得。

## 清华大学GPA查询

介绍参考上一节。

在「INFO-全部成绩」页面计算各个学期以及总的的必限以及必限任的GPA。脚本地址在[此](https://greasyfork.org/zh-CN/scripts/420540-清华大学gpa查询)

## 清华大学一体化平台视频自动播放

脚本在[此](https://github.com/Co1lin/Tsinghua-Yukuotang-Autoplay)，可自动播放 [tsinghua.yuketang.cn](https://github.com/Co1lin/Tsinghua-Yukuotang-Autoplay/blob/main/tsinghua.yuketang.cn) 上的课程视频。

## 学堂在线视频自动播放

还在后台刷慕课时经常查看是否停止吗，一个脚本帮你自动播放下一课！

脚本在[此](https://greasyfork.org/en/scripts/373881-清华学堂在线视频自动播放)

由于该脚本历史较久，较久未维护，且也存在一些bug，不保证其长期的可用性。发现问题时或改进代码时可联系原作者 @RikaSugisawa

## 学堂在线字幕下载器

还在准备复习的时候一个个翻视频下载字幕吗？这个脚本帮你忙！

Rabbit Hu 版本：脚本在[此](https://greasyfork.org/zh-CN/scripts/408878-xuetangx-caption-crawler)，项目地址在[此](https://github.com/Rabbit-Hu/xuetangx-caption-crawler)。

Roberts Holder 版本：项目地址在[此](https://github.com/rcy17/MOOC_subtitle_spider)

Rynco Maekawa 版本：项目地址在[此](https://github.com/lynzrand/xuetangx_sub)

## 清华教学参考书爬取

引自原文：最近疫情严重，购买教材较为困难，为了方便大家在线学习，写了一个爬取清华教参的 python 脚本。

项目地址在[此](https://github.com/lflame/TsinghuaBookCrawler)

又有一种实现

引用原文：自动下载书籍每一页的原图。

项目地址在[此](https://github.com/i207M/reserves-lib-tsinghua-downloader)

## 课程地点分享

在[https://wmcgcdn.rika.tech/](https://wmcgcdn.rika.tech/)中，其项目地址为[此](https://github.com/RikaKagurasaka/where-my-course-gone-backend)。

目前已经停止维护与运营。

## 清华大学计算机系课程攻略

[GitHub地址](https://github.com/PKUanonym/REKCARC-TSC-UHT)与[校内地址](https://git.tsinghua.edu.cn/pkuanonym/REKCARC-TSC-UHT)

## 校园网认证工具汇总

本着用轮子不如造轮子的精神，一代代清华人与校园网斗智斗勇，开发了无数认证工具，我们在此尽可能列出它们，供大家根据喜好选用。

| 项目链接 | 支持平台 | 实现语言 | 目前是否可用（是否被维护）| 特性 |
| --- | --- | --- | --- | --- |
| [Tunet-2018 (official)](https://its.tsinghua.edu.cn/xywl/xywsyzn/yxw_hkhd_/khdxz.htm) | Windows-GUI, Linux-CLI | 未知 | 在2020年暑假的`ac_id`升级后不可用 | 未调查 |
| [GoAuthing](https://github.com/z4yx/GoAuthing/) | Linux-CLI (x86\_64, arm, mips, ppc), Windows-CLI, Mac OS-CLI (Intel, Apple) | Go | 可用 | 全平台全架构，准入与准出，v4和v6，systemd 服务，TUNA 提供[镜像](https://mirrors.tuna.tsinghua.edu.cn/github-release/z4yx/GoAuthing/LatestRelease/)可以在未认证时下载认证工具，提供认证相关库 |
| [tunet-python](https://github.com/yuantailing/tunet-python) | 支持 python 的平台，CLI | Python | 可用 | v4与v6，准入与准出，流量与准入出状态监控 |
| [auth-tsinghua](https://github.com/jiegec/auth-tsinghua) | 支持 node.js 的平台, CLI | Javascript | 不再维护 | 已经重定向至 GoAuthing |
| [TsinghuaNet](https://github.com/Berrysoft/TsinghuaNet) | Windows, Mac OS, Linux, UWP, Android, iOS | .NET | 可用 | 真全平台，流量与余额监控，准入与准出，v4与v6，提供认证相关库 |
| [tunet-cli](https://github.com/syimyuzya/tunet-cli) | 支持 python 的平台，CLI | Python | 不再维护，上个 commit 在2017年 | 未调查 |
| [Tsinghua-Online](https://github.com/xxr3376/Tsinghua-Online) | 浏览器插件，在[Chrome 商店](https://chrome.google.com/webstore/detail/tsinghua-online/elkbekfdkihpbcbacmppemegcekohkjo)中 | Javascript | 不再维护，上个 commit 在2013年 | 浏览器插件 |
| [tunet-c](https://github.com/robertying/tunet-c) | OpenWRT, Linux, macOS; CLI | C | 可用 | 提供认证相关库，二进制文件较小 |
| [TsinghuaTunet](https://github.com/WhymustIhaveaname/TsinghuaTunet) | 支持 python 的平台， CLI | Python | 可用于特定子网 | 未调查 |
| [THUNetwork](https://github.com/zhaofeng-shu33/THUNetwork) | 支持 python 的平台， CLI | Python | 不再维护 | 密码明文传入命令行，较为不安全 |
| [tunet-rust](https://github.com/Berrysoft/tunet-rust) | Windows, Mac OS, Linux | Rust | 可用 | 流量与余额监控，准入与准出，v4与v6，提供认证相关库 |

## INFO/网络学堂 APP/插件

本着用轮子不如造轮子的精神，一代代清华人与INFO与网络学堂斗智斗勇，开发了无数易用工具，我们在此尽可能列出它们，供大家根据喜好选用。

| 项目链接 | 支持平台 | 实现语言 | 目前是否可用（是否被维护）| 特性 |
| --- | --- | --- | --- | --- |
| [INFO](http://info.tsinghua.edu.cn/) | 网页 | 未调查 | 能用 | 官方网页 |
| [LEARN](http://learn.tsinghua.edu.cn/) | 网页 | 未调查 | 能用 | 官方网页 |
| [Learn-Project](https://github.com/xxr3376/Learn-Project) | 浏览器插件 | Typescript | 可用 | 按照时间线与种类排列网络学堂项目，在谷歌，火狐以及 Edge 的插件商店中，现代前端 |
| [LearnX](https://github.com/robertying/learnX) | iOS,ipad OS, macOS, Android | React | 可用 | 项目开源许可证，其余参见项目介绍 |
| [THUInfo](https://github.com/UNIDY2002/THUInfo) | 移动端APP | Typescript | 可用 | 拥有苹果应用商店分发，包括家园，学生部（教室），图书馆的项目，支持树洞 |
| AtTsinghua | 移动端APP | 未知 | 未知 | 拥有苹果应用商店分发，其余未调查，为某实验室校庆作品 |
| [learn2018-autodown](https://github.com/Trinkle23897/learn2018-autodown) | 支持 Python 的平台 | Python | 可用 | 真全部信息/文件下载（其余详见项目介绍） |

## 注册标志（用于火车票）

参考[此网站](https://tuixue.online/zcimage/)，方便在校外时获取相关注册标志。

## 寝室电费查询

有通过 headless Chrome 的[实现](https://github.com/WhymustIhaveaname/TsinghuaElectric)

也有另一种实现，参考 aux 目录中的 `TsinghuaElectricityBillChecker.py`，用户需要修改一些内嵌的参数。

通过这些脚本可以将数据灌入 grafana 中，实现电费监控与报警。

## 清华上下课铃声

在家学习没氛围，想念学校自习室？清华铃声软件帮您忙！

目前有 macOS 版本，项目[在此](https://github.com/LyricZhao/THU-Bell)

## 随机选择校内餐厅

食堂太多不知道去哪吃？随机数发生器帮您忙！

项目在[此](https://github.com/SuXY15/RandomCanteen)

小程序二维码

![](https://raw.githubusercontent.com/SuXY15/MyPic/master/RandomCanteen/RandomCanteen.jpg)

## 华清大学课程攻略共享计划

面向全校同学的课程攻略共享计划，旨在消除学习资源的信息不对称，促进学习资源和资料的开放共享。项目[在此](https://closed.social/pastExam/)。相较之 GitHub，分享与下载操作对不熟悉技术的同学都更加友好，欢迎分享！

![华清大学课程攻略共享计划](image/course_strategy.jpg)

## 雨课堂课件下载器

目前仅适用于「长江雨课堂」，不过改改就可以用于荷塘雨课堂。

项目地址在[此](https://github.com/ShevonKuan/yuektang_ppt2pdf)。
