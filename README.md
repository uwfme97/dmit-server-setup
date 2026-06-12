# DMIT 教程完全指南：从注册购买到 SSH 连接，新手也能轻松上手

刚接触 DMIT 的人，第一个问题往往不是"它好不好用"，而是"这玩意儿怎么用"。

这很正常。DMIT 跟那些傻瓜式主机不一样——它用的是 SSH 密钥登录，没有传统的用户名密码那套，第一次上手确实有点懵。但说实话，一旦搞清楚流程，它其实挺顺手的，而且安全性比密码登录高多了。

这篇文章就是给你准备的：从注册账号、选套餐、到 SSH 连接、快照备份，全流程手把手讲清楚。

---

## DMIT 是什么？为什么值得用？

DMIT 是一家成立于 2018 年的美国注册 VPS 服务商，总部在纽约。它主营香港、洛杉矶（LAX）、东京（TYO）三个数据中心的 KVM VPS，底层用的是 AMD EPYC 高性能处理器加企业级 SSD。

讲人话就是：硬件不错，线路更不错。

DMIT 最被中国用户看重的，是它的 CN2 GIA 和 CMIN2 优化线路。这两条线路对国内访问速度有明显的提升，不管是建站、搭服务、还是做跨境业务，延迟都比普通 VPS 低得多。

它的产品线分三个档次：

- **Premium（旗舰）**：CN2 GIA / CMIN2 优化，适合对速度敏感的业务
- **Eyeball（眼球）**：性价比更高，带宽更大，适合流量大的场景
- **Tier 1（基础）**：国际线路，价格最亲民，适合对国内访问要求不高的用途

---

## 第一步：注册账号

打开 👉 [DMIT 官网注册](https://www.dmit.io/aff.php?aff=18446)，点击右上角的 **Register**。

填写邮箱、密码、姓名，提交后去邮箱确认注册链接。整个过程两分钟搞定，不需要填什么复杂信息。

> 建议用常用邮箱注册，因为 SSH 密钥、账单通知都会发到这个邮箱，别用临时邮箱凑合。

---

## 第二步：选套餐

DMIT 的套餐比较多，按数据中心 + 网络类型来划分。下面把主要套餐梳理成一张表，方便对比：

### 洛杉矶（LAX）- Premium 旗舰线路（CN2 GIA）

| 套餐名 | CPU | 内存 | SSD | 流量 | 带宽 | 价格 | 购买 |
|--------|-----|------|-----|------|------|------|------|
| TINY | 1核 | 2GB | 20GB | 1000GB | 1Gbps | $37.99/季 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=183) |
| Pocket | 2核 | 2GB | 40GB | 1500GB | 4Gbps | $56.70/季 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=184) |
| STARTER | 2核 | 2GB | 80GB | 3000GB | 10Gbps | $38.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=185) |
| MINI | 4核 | 4GB | 80GB | 5000GB | 10Gbps | $76.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=186) |
| MICRO | 4核 | 4GB | 160GB | 7000GB | 10Gbps | $99.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=187) |
| MEDIUM | 6核 | 8GB | 160GB | 15000GB | 10Gbps | $219.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=188) |
| LARGE | 8核 | 16GB | 320GB | 25000GB | 10Gbps | $459.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=189) |
| GIANT | 12核 | 24GB | 640GB | 50000GB | 10Gbps | $839.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=190) |

**不限流量选项（LAX Premium）：**

| 套餐名 | CPU | 内存 | SSD | 带宽 | 价格 | 购买 |
|--------|-----|------|-----|------|------|------|
| uMINI | 2核 | 2GB | 40GB | 30Mbps 不限流量 | $239.99/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=191) |
| uMICRO | 4核 | 8GB | 80GB | 50Mbps 不限流量 | $399.99/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=192) |
| uMEDIUM | 4核 | 8GB | 120GB | 100Mbps 不限流量 | $799.99/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=193) |
| uLARGE | 8核 | 16GB | 240GB | 200Mbps 不限流量 | $1399.99/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=194) |

### 洛杉矶（LAX）- Tier 1 经济线路（入门首选）

| 套餐名 | CPU | 内存 | SSD | 流量 | 带宽 | 价格 | 购买 |
|--------|-----|------|-----|------|------|------|------|
| WEE | 1核 | 1GB | 20GB | 1000GB | 1Gbps | $36.90/年 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=167) |
| TINY | 1核 | 1GB | 20GB | 2000GB | 1Gbps | $6.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=168) |
| STARTER | 2核 | 2GB | 40GB | 4000GB | 2Gbps | $12.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=169) |
| MINI | 2核 | 4GB | 60GB | 6000GB | 4Gbps | $21.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=170) |
| MICRO | 4核 | 4GB | 80GB | 8000GB | 4Gbps | $32.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=171) |
| MEDIUM | 4核 | 8GB | 100GB | 12000GB | 4Gbps | $54.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=172) |
| LARGE | 8核 | 16GB | 200GB | 20000GB | 4Gbps | $99.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=173) |
| GIANT | 16核 | 32GB | 400GB | 40000GB | 4Gbps | $199.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=174) |

### 香港（HKG）- Premium 旗舰线路

| 套餐名 | CPU | 内存 | SSD | 流量 | 价格 | 购买 |
|--------|-----|------|-----|------|------|------|
| TINY | 1核 | 1GB | 20GB | 500GB | $39.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=195) |
| STARTER | 2核 | 2GB | 40GB | 1000GB | $79.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=196) |
| MINI | 2核 | 4GB | 60GB | 2000GB | $149.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=197) |
| MICRO | 4核 | 4GB | 80GB | 3000GB | $219.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=198) |
| MEDIUM | 4核 | 8GB | 120GB | 4000GB | $299.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=199) |
| LARGE | 8核 | 16GB | 240GB | 5000GB | $399.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=200) |
| GIANT | 8核 | 24GB | 480GB | 6000GB | $499.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=201) |

### 东京（TYO）- Premium 旗舰线路（性价比最高）

| 套餐名 | CPU | 内存 | SSD | 流量 | 价格 | 购买 |
|--------|-----|------|-----|------|------|------|
| TINY | 1核 | 1GB | 20GB | 500GB | $21.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=202) |
| STARTER | 2核 | 2GB | 40GB | 1000GB | $42.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=203) |
| MINI | 2核 | 4GB | 60GB | 2000GB | $84.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=204) |
| MICRO | 4核 | 4GB | 80GB | 3000GB | $128.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=205) |
| MEDIUM | 4核 | 8GB | 120GB | 4500GB | $189.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=206) |
| LARGE | 8核 | 16GB | 240GB | 6000GB | $359.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=207) |
| GIANT | 12核 | 32GB | 480GB | 10000GB | $799.90/月 | 👉 [立即购买](https://www.dmit.io/aff.php?aff=18446&pid=208) |

> **怎么选？** 预算有限的新手直接上 LAX Tier 1 WEE（年付 $36.9），够用、够便宜、够练手。要求速度快、对国内访问友好的，选 TYO Premium TINY（月付 $21.9），性价比最高的 CN2 GIA 入门款。

---

## 第三步：下单购买

选好套餐后，点进去会让你配置一些参数：

1. **Hostname**：随便填，比如 `myserver.com`，只是本地标记用
2. **Root Password**：设置 root 密码，建议搞复杂点，大小写加数字
3. **操作系统**：默认 Debian 11，不熟悉的话就用默认的
4. **计费周期**：月付、季付、年付，周期越长折扣越多

填完加入购物车，去结算页面。**支持支付宝付款**，对国内用户非常友好。

如果有优惠码记得在结算页面输入，有时候能便宜不少。

👉 [点击前往选购 DMIT VPS](https://www.dmit.io/aff.php?aff=18446)

---

## 第四步：获取 SSH 密钥

这里是新手最容易卡壳的地方。

**DMIT 的 VPS 默认不用密码登录，用的是 SSH 密钥认证。** 这个设计更安全，但第一次用的人会有点懵。

### 下载密钥

VPS 开通后，你会收到一封邮件，里面有管理面板链接。登录面板，找到刚购买的 VPS，第一次点进去**会自动弹出 SSH Key 下载弹窗**。

> **超级重要**：这个密钥只能下载一次！如果你直接关掉了，就只能去面板重新生成。所以一定要在这个弹窗里点 "Download private key" 把文件保存好。

下载下来是一个压缩包，解压后有两个文件夹：
- `private_key/`：里面有 `id_rsa.pem`（给 Linux/Mac 用）和 `id_rsa.ppk`（给 PuTTY 用）
- `public_key/`：公钥，一般不需要手动操作

---

## 第五步：SSH 连接

### Windows 用户

**方法一：用 XShell（推荐新手）**

1. 打开 XShell，新建连接
2. 主机填你的 VPS IP，端口填 22
3. 认证方式选 **Public Key（公钥认证）**
4. 导入私钥文件（`id_rsa.ppk`）
5. 用户名填 `root`
6. 点连接

**方法二：用 PuTTY**

1. 打开 PuTTYgen，加载 `id_rsa.ppk` 文件（或者把 `.pem` 转换成 `.ppk`）
2. 打开 PuTTY，填入 IP 和端口
3. 在 Connection > SSH > Auth 里导入私钥
4. 连接

**方法三：PowerShell / CMD（Windows 10/11 自带 OpenSSH）**

bash
ssh -i "C:\path\to\id_rsa.pem" root@你的IP地址


### Mac / Linux 用户

终端直接搞定：

bash
# 先给私钥文件设置正确权限
chmod 600 /path/to/id_rsa.pem

# SSH 连接
ssh -i /path/to/id_rsa.pem root@你的IP地址


第一次连接会问你是否信任这个主机，输入 `yes` 回车就行。

---

## 第六步：Termius 连接（跨平台推荐）

Termius 是 DMIT 官方知识库里推荐的 SSH 工具，支持 Windows、Mac、iOS、Android，界面比 PuTTY 好看很多。

DMIT 官方教程里有详细的 Termius 配置步骤：

1. 在 Termius 里新建 Host，填入 IP
2. 认证方式选 Key
3. 导入 `id_rsa.pem` 私钥文件
4. 保存并连接

---

## 实用管理技巧

### 快照备份

DMIT 给每个 VPS **免费送一个快照额度**，别浪费了。

最佳实践是：系统装完、基础环境配好之后，马上做一个快照。以后不管怎么折腾——装软件、改配置、测试新东西——如果搞崩了，一键恢复，五分钟之内回到正常状态。

在 DMIT 管理面板里找到你的 VPS，点 **Snapshot** 选项卡，点 "Create Snapshot" 就行。

### 流量查看

DMIT 的流量计费方式要注意看清楚：

- **Premium 和 Tier 1 套餐**：一般是单向计费（只算出站或者只算入站，哪个大算哪个）
- **Eyeball 套餐**：要看具体套餐说明

在管理面板的 Overview 页面可以实时查看流量使用情况，临近用完记得续费或者升级套餐，流量超标会被限速。

### 重启与重装系统

- **重启**：面板里点 Reboot，正常情况下几十秒内完成
- **重装系统**：选 Reinstall，可以换其他 Linux 发行版。注意重装会清空数据，做快照或者备份再操作

### 设置 root 密码登录（可选）

DMIT 默认只支持密钥登录。如果你确实需要密码登录（比如某些面板软件要求），可以 SSH 连上去之后手动开启：

bash
# 修改 SSH 配置
nano /etc/ssh/sshd_config

# 把这行改为 yes
PasswordAuthentication yes

# 重启 SSH 服务
systemctl restart sshd


但强烈建议保持密钥登录，安全性高很多。

---

## 常见问题

**Q：SSH 密钥弹窗没保存，怎么办？**

去管理面板，找到 VPS 详情，在密钥管理里点 "Regenerate"，系统会生成新密钥，下载保存好。

**Q：连接 SSH 一直超时怎么办？**

1. 检查 IP 是否正确
2. 确认端口是 22
3. 检查防火墙是否放行了 22 端口
4. 如果在中国大陆，尝试换时段，部分地区运营商对某些 IP 段有临时干扰

**Q：流量快用完了怎么办？**

在面板里可以单独购买额外流量包，或者直接升级到更高配置的套餐。不要等流量跑完，限速之后会非常慢。

**Q：支持什么支付方式？**

支付宝、PayPal、信用卡都支持。国内用户用支付宝最方便，无需汇率换算。

---

## 总结：DMIT 适合谁用？

| 用途 | 推荐线路 | 推荐套餐 |
|------|----------|----------|
| 个人学习 / 练手 | LAX Tier 1 | WEE（$36.9/年） |
| 个人建站 | TYO Premium | TINY（$21.9/月） |
| 国内访问速度优先 | LAX / TYO Premium | TINY 起步 |
| 大流量业务 | LAX Eyeball | STARTER 起步 |
| 企业级应用 | 任意 Premium | MEDIUM 以上 |

DMIT 的核心竞争力在于线路质量，CN2 GIA 对国内用户来说确实明显比普通线路快。如果你的主要用户在中国大陆，或者你自己经常需要从国内访问 VPS，DMIT 是值得考虑的选择。

价格方面，它不算便宜，但也不算贵——对标同等线路质量的竞品，DMIT 的价格其实相当有竞争力，尤其是东京 Premium 系列，入门价格很能打。

👉 [前往 DMIT 官网查看最新优惠](https://www.dmit.io/aff.php?aff=18446)
