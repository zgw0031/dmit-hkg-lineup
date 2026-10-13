# 香港 VPS：DMIT 三条线路怎么挑？Pro、Eyeball、Tier 1 全套餐价格与延迟对比

搜“香港 VPS”的人，需求通常不是同一种。有人机房放在香港，但用户全在欧美，要的是国际带宽和便宜流量；有人客户在国内，页面晚高峰一卡就掉单，愿意为延迟多花钱；还有人是拿香港机器做中转、做落地、跑东南亚业务。这三种需求，落到 DMIT 香港机房上，指向的是三条完全不同的线路。

先把结论放前面：DMIT 香港（HKG，机房在 Equinix HK2）目前对外卖三个系列——Tier 1、Eyeball、Premium。硬件都是 KVM 虚拟化 + AMD EPYC + SSD，标配 1 个 IPv4 和 1 个 IPv6 /64，差别几乎全在网络线路上。选错了不会退钱，只会让你的用户打开页面时多等半秒。

## 三条线路，差的是路由不是配置

| 系列 | 产品代号 | 中国大陆访问 | 主要场景 |
| --- | --- | --- | --- |
| Tier 1 | HKG.AS3.T1 | 无专项优化，走国际线路 | 面向海外用户、大流量业务、自己已有中转方案 |
| Eyeball | HKG.EB（AS3 / AN5 平台） | 尽力优化，移动方向表现较好 | 预算有限但必须落在香港 |
| Premium | HKG.Pro（常规产品已升级 AN5 平台） | 三网 CN2 GIA 回程，最优 | 用户主要在中国大陆、对延迟敏感 |

Premium 是三条线里对国内最友好的：电信去程 CN2 GIA 直连香港 CTG，回程同样接 CN2 GIA；联通走 AS4837 + AS10099；移动走香港 CMI 直连。第三方测评里，这一档到国内主要城市的 Ping 通常在 50ms 以内，北上广深落在 30–45ms 区间，晚高峰的丢包控制得比较好。

Eyeball 的位置在中间。回程是联通 CUG 与 CMI 动态负载、移动 CMI、电信 163，去程电信走 CN2，联通和移动没有做优化。它比 Tier 1 稳定，比 Premium 便宜，流量也给得更宽松。

Tier 1 是纯国际线路，接入了 RETN 等国际骨干，香港到欧洲的延迟表现不错。要提醒的是：它对中国大陆没有优化，电信、联通用户的体验可能比走美西还差。如果你的客户在国内，别因为便宜就买 T1。

想先自测再决定，可以用这几个测试 IP：Premium 用 103.117.100.199，Eyeball 用 154.12.188.3（另有 191.222.220.220），Tier 1 用 191.223.210.210。DMIT 也有公开的 Looking Glass 页面可以直接跑路由追踪。

## DMIT 香港全套餐价格表

下面按系列分开列。需要提前说明一件事：DMIT 香港库存波动很大，经常出现整条产品线断货数周、补货几天就售空的情况，套餐配置和价格也调整得比较频繁。表格里的数据来自近期公开的套餐信息，最终下单页显示的价格和库存才算数。

### 一、HKG Tier 1（国际线路，AMD EPYC 7003）

| 套餐 | CPU / 内存 / 硬盘 | 月流量 @ 端口 | 超量后 | 计费周期与价格 | 购买 |
| --- | --- | --- | --- | --- | --- |
| HKG.T1.WEE | 1核 / 1G / 20G | 1TB @ 4Gbps | 限速 50Mbps 不限量 | 年付 $36.90 | [ 以 $36.9/年入手香港 T1 入门款](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.TINY | 1核 / 1G / 20G | 2TB @ 4Gbps | 限速 100Mbps 不限量 | 月付 $6.90 / 年付 $76.90 | [ 查看 HKG.T1.TINY 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.STARTER | 1核 / 2G / 40G | 4TB @ 10Gbps | 限速 100Mbps 不限量 | 月付 $12.90 / 年付 $154.80 | [ 查看 HKG.T1.STARTER 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.MINI | 2核 / 2G / 60G | 8TB @ 10Gbps | 限速 100Mbps 不限量 | 月付 $21.90 / 年付 $262.80 | [ 查看 HKG.T1.MINI 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.MICRO | 4核 / 4G / 80G | 16TB @ 10Gbps | 限速 200Mbps 不限量 | 月付 $32.90 | [ 查看 HKG.T1.MICRO 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.MEDIUM | 4核 / 8G / 160G | 32TB @ 10Gbps | 限速 200Mbps 不限量 | 月付 $49.90 | [ 查看 HKG.T1.MEDIUM 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.LARGE | 8核 / 16G / 320G | 64TB @ 10Gbps | 限速 500Mbps 不限量 | 月付 $99.90 | [ 查看 HKG.T1.LARGE 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.T1.GIANT | 8核 / 24G / 640G | 128TB @ 10Gbps | 限速 1Gbps 不限量 | 月付 $199.90 | [ 查看 HKG.T1.GIANT 配置](https://www.dmit.io/aff.php?aff=12046) |

T1 系列有个设计挺少见：流量跑完不会直接停机，而是降到限速模式继续跑。WEE 限 50Mbps，TINY 到 MINI 限 100Mbps，往上依次放宽。做下载站、做备份、跑爬虫的人应该能理解这意味着什么——月底流量见底的时候，服务还活着。

### 二、HKG Eyeball（尽力优化，分 AS3 与 AN5 两个平台）

AS3 平台用 AMD EPYC 7003，起步门槛最低；AN5 平台用 EPYC 9005 + DDR5，规格从 4 核起步，面向算力和并发要求更高的场景。

**AS3 平台**

| 套餐 | CPU / 内存 / 硬盘 | 月流量 @ 端口 | 计费周期与价格 | 购买 |
| --- | --- | --- | --- | --- |
| HKG.AS3.EB.WEE | 1核 / 1G / 20G | 500GB @ 500Mbps | 月付 $24.90 | [ 查看 Eyeball 最低门槛方案](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AS3.EB.TINY | 1核 / 1G / 20G | 800GB @ 1Gbps | 月付 $39.90 | [ 查看 HKG.AS3.EB.TINY 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AS3.EB.STARTER | 1核 / 2G / 40G | 1.5TB @ 1Gbps | 月付 $79.90 | [ 查看 HKG.AS3.EB.STARTER 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AS3.EB.MINI | 2核 / 4G / 60G | 2.2TB @ 1Gbps | 月付 $126.90 | [ 查看 HKG.AS3.EB.MINI 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AS3.EB.MICRO | 4核 / 4G / 80G | 3TB @ 1Gbps | 月付 $179.90 | [ 查看 HKG.AS3.EB.MICRO 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AS3.EB.MEDIUM | 4核 / 8G / 160G | 4TB @ 1Gbps | 月付 $239.90 | [ 查看 HKG.AS3.EB.MEDIUM 配置](https://www.dmit.io/aff.php?aff=12046) |

**AN5 平台**

| 套餐 | CPU / 内存 / 硬盘 | 月流量 @ 端口 | 计费周期与价格 | 购买 |
| --- | --- | --- | --- | --- |
| HKG.AN5.EB.TINY | 4核 / 4G / 80G | 2.2TB @ 1Gbps | 月付 $149.90 | [ 查看 AN5 平台 Eyeball 入门档](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.EB.STARTER | 4核 / 4G / 160G | 3TB @ 1Gbps | 月付 $199.90 | [ 查看 HKG.AN5.EB.STARTER 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.EB.MINI | 6核 / 8G / 160G | 4TB @ 1Gbps | 月付 $279.90 | [ 查看 HKG.AN5.EB.MINI 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.EB.LARGE | 8核 / 16G / 320G | 4.5TB @ 1Gbps | 月付 $359.90 | [ 查看 HKG.AN5.EB.LARGE 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.EB.GIANT | 12核 / 24G / 640G | 9TB @ 1Gbps | 月付 $759.90 | [ 查看 HKG.AN5.EB.GIANT 配置](https://www.dmit.io/aff.php?aff=12046) |

> DMIT 官方目前仍把香港 Eyeball 标为 Beta，路由和产品规格处于持续调整状态。如果你的业务对线路固定性要求很高，官方本身的表述就是不建议直接拿它替代 Premium。

### 三、HKG Premium（CN2 GIA，常规产品已升级 AN5 平台）

原来的 HKG.Pro 常规产品已经整体切到 AN5 平台（AMD EPYC 9005 系列，DDR5 5600），价格没跟着涨，仍是月付 $39.90 起。被排除在这次升级之外的，只有部分折扣款套餐。

| 套餐 | CPU / 内存 / 硬盘 | 月流量 @ 端口 | 计费周期与价格 | 购买 |
| --- | --- | --- | --- | --- |
| HKG.AN5.Pro.TINY | 1核 / 1G / 20G | 500GB @ 1Gbps | 月付 $39.90 | [ 以 $39.9/月入手香港 CN2 GIA](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.Pro.STARTER | 1核 / 2G / 40G | 1TB @ 1Gbps | 月付 $79.90 | [ 查看 HKG.AN5.Pro.STARTER 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.Pro.MINI | 2核 / 2G / 60G | 1.5TB @ 1Gbps | 月付 $119.90 | [ 查看 HKG.AN5.Pro.MINI 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.Pro.MICRO | 2核 / 4G / 80G | 2TB @ 1Gbps | 月付 $159.90 | [ 查看 HKG.AN5.Pro.MICRO 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.Pro.MEDIUM | 4核 / 4G / 160G | 2.5TB @ 1Gbps | 月付 $179.90 | [ 查看 HKG.AN5.Pro.MEDIUM 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.Pro.LARGE | 4核 / 8G / 240G | 3TB @ 1Gbps | 月付 $239.90 | [ 查看 HKG.AN5.Pro.LARGE 配置](https://www.dmit.io/aff.php?aff=12046) |
| HKG.AN5.Pro.GIANT | 8核 / 16G / 320G | 6TB @ 1Gbps | 月付 $499.90 | [ 查看 HKG.AN5.Pro.GIANT 配置](https://www.dmit.io/aff.php?aff=12046) |

## 同价位对比：贵的那部分买到了什么

把几组价格放在一起看，选择逻辑会清楚很多。

$39.90 这个价位，Premium 的 TINY 给你 1核1G 和 500GB 流量，Eyeball 的 TINY 同样 1核1G，流量是 800GB。也就是说，Premium 多出来的钱没有换成配置，全部换成了 CN2 GIA 的路由保证。如果你的页面在国内打开速度直接决定转化，这笔钱花得下去；如果访问者主要在海外，多付的部分基本是浪费。

Eyeball 的 WEE 是 $24.90/月，比 Premium 最低档还便宜 15 美元，但它只有 500Mbps 端口和 500GB 流量。跑小站、个人服务、轻量 API 够用，跑不动视频类或大流量的业务。

T1 那边的价格结构完全不同。WEE 年付 $36.90，折下来每月约 3 美元，还带 1TB 月流量和 4Gbps 端口；TINY 月付 $6.90 给 2TB。如果你本来就有中转方案，或者客户在地图上根本不在亚洲，T1 的性价比是这三条线里最突出的——前提是你接受它对中国大陆没有优化这件事。

年付值不值也要分开算。T1.TINY 月付 $6.90，年付 $76.90，比 12 个月月付（$82.80）省了约 7 美元。Premium 的钱基本没差：TINY 月付 $39.90，年付 $478，按 12 个月算 $478.80，省下的钱可以忽略。所以在 Premium 线上，年付的主要意义不是省钱，而是锁定库存——香港 Pro 的货经常断。

## 优惠码这件事，最好自己验一次

DMIT 没有长期公开的优惠码清单，促销基本是限时、限量、限定产品线的组合。流传在第三方站点上的折扣信息互相矛盾：有人整理出针对 HKG T1 年付的循环折扣码，也有站点直接写着“目前暂无公开优惠码”。这两类说法之间，你没法靠读文章判断谁对。

能确认的判断方法只有一个：在购买页选好套餐和付款周期后，把优惠码填进 Validate Code 那一栏点验证。能不能用、打完折多少钱，购物车会直接告诉你，比任何测评文章都准。循环折扣（recurring）和一次性折扣的区别也在这里——前者续费同样打折，后者只影响首单，续费时价格会跳回去。

付款方面，DMIT 支持支付宝、微信支付和 PayPal，对国内用户没有门槛。

> 香港机房补货节奏很不规律，曾经出现整条产品线断货三个月、补货三天售空的情况。如果你已经确定要哪一档，等的时间成本往往比省几美元更贵。

## 别踩这几个坑

最常见的错误是拿 T1 去服务国内用户。T1 是国际线，RETN 优化的是香港到欧洲这一段，中国大陆方向没有做任何专项处理。电信用户买 T1，延迟可能比用美西机房还高。

第二个是把 Eyeball 当成 Premium 的平替。EB 的定位是“在成本和大陆访问体验之间折中”，官方自己也标注了 Beta 状态，路由可能继续调整。省下的钱是真的，线路稳定性上的不确定性也是真的。

第三个是忽略库存的时效性。这篇文章里所有价格和配置都可能在你读到的时候已经变了，尤其是流量额度和端口带宽这两项，DMIT 在不同批次之间调整过。下单前花一分钟核对购买页，比事后发现配置不一样要省事。

## 该选哪一档

用户在中国大陆、网站速度直接影响收入，选 Premium，从 TINY 起试，流量不够再往上换。国内访问是刚需但预算卡得紧，选 Eyeball，先看清楚 Beta 提示能不能接受。业务面向海外、有自己的中转方案、或者只是需要一个大带宽的香港出口，T1 是这三条线里最划算的一条。

拿不准的话，最省事的办法是把 DMIT 香港三条线路的套餐页和实时库存都打开对比一遍：

👉 [👉 查看 DMIT 香港 VPS 全部套餐与当前库存](https://www.dmit.io/aff.php?aff=12046)

价格和库存都摆在一起的时候，选择通常不需要纠结太久。
