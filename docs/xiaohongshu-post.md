# 小红书发布稿：Codex Token Monitor

## 标题备选

1. 我给 Codex 做了一个本地 token 仪表盘
2. 每天用了多少 Codex，终于能看清楚了
3. 一个 Mac 菜单栏里的 Codex 用量监控器
4. Codex Pro 用户可能会喜欢的小工具

## 图文页 1：封面

标题：

我给 Codex 做了一个本地 token 监控器

副标题：

能看到今天花了多少、用了多少 token、5h / 1w 额度还剩多少

正文短句：

最近总觉得 Codex 用量消失得很快，但官方界面给我的颗粒度又不够细。

于是我做了一个本地小工具：读取 `~/.codex/sessions`，把 token、缓存命中、费用估算和额度窗口都展示出来。

配图建议：

使用 `docs/images/dashboard-top.png`。封面可裁掉一部分底部，只保留标题、四个状态卡、核心指标和额度窗口。

## 图文页 2：它能看什么

标题：

我最想看的几个数字都放进去了

正文：

- 今天预估花费
- 今天 / 近 7 天 / 近 30 天 / 本月 token
- input、cached input、output 分项费用
- cache hit rate 和 reasoning tokens
- 5h primary / 1w secondary 额度窗口
- Mac 菜单栏常驻显示 `$ / tokens / 5h% / 1w%`

补充说明：

费用默认按 GPT-5.5 估算，也可以在 Dashboard 里切换模型。菜单栏上的额度百分比会按使用率从薄荷绿逐渐变到玫红。

配图建议：

使用 `docs/images/menu-bar-compact.png` 和 `docs/images/menu-bar-dropdown.png`，可以拼成一张小图放在页面右侧或下方。

## 图文页 3：开源和注意事项

标题：

本地运行，不上传 session

正文：

项目是开源的，安装后会启动两个本地服务：

```bash
git clone https://github.com/uohzey0519/codex-token-monitor.git
cd codex-token-monitor
npm run install:macos
```

打开 Dashboard：

```text
http://127.0.0.1:48731
```

数据默认只在本机读取和展示，HTTP 服务绑定在 `127.0.0.1`。

需要注意：

`total tokens`、缓存命中和预估费用通常会随着当前 working turn 持续更新；额度窗口不是实时余额，而是 Codex 写进 session 的 `rate_limits` 快照，可能要等当前 turn 结束或后端 checkpoint 后才刷新。

配图建议：

使用 `docs/images/dashboard-bottom.png`，展示按月概览和高峰日期/线程。

## 正文 Caption

最近我一直在用 Codex，尤其换到 Pro 之后，总感觉额度消耗和自己的直觉有点对不上。

于是顺手做了一个小工具：Codex Token Monitor。

它会读取本机 `~/.codex/sessions` 里的 session JSONL，做一个本地 Dashboard，还会在 Mac 菜单栏显示今天的预估费用、total tokens、5h primary 和 1w secondary 的额度百分比。

我自己主要用它看三件事：

1. 今天大概用了多少钱
2. token 到底花在 input、cached input 还是 output 上
3. 5h / 1w 额度窗口现在大概到哪里了

一个比较重要的细节：费用和 token 用量通常会随着 working turn 写入持续更新，但额度窗口不是实时余额，它来自 Codex 写入 session 的快照，所以可能会比你当前体感慢几十秒到一分钟。

项目已经放到 GitHub，Mac + Node.js 20+ 可以直接安装：

```bash
git clone https://github.com/uohzey0519/codex-token-monitor.git
cd codex-token-monitor
npm run install:macos
```

本地打开：

```text
http://127.0.0.1:48731
```

适合和我一样经常用 Codex，又想知道自己到底把 token 用到哪里的人。

## 标签建议

#Codex #AI工具 #程序员工具 #效率工具 #Mac效率 #开源项目 #AI编程 #Token监控 #开发者工具

## 发布备注

- 小红书正文里建议不要放太多命令，可以把安装命令放在最后。
- 如果担心链接不可点，可以在评论区补 GitHub 仓库名：`uohzey0519/codex-token-monitor`。
- 三页图文最简顺序：`dashboard-top.png`、菜单栏拼图、`dashboard-bottom.png`。
