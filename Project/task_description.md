# 任务介绍：赛制

[TOC]



## 赛题简介

新浪微博作为中国最大的社交媒体平台，旨在帮助用户发布的公开内容提供快速传播互动的通道，提升内容和用户的影响力。本次赛题的目标是发现能够最快找到有价值微博的方法，然后应用于平台的内容分发控制策略，对于有价值的内容可以增加曝光量，提高内容的传播互动量。

新人实战前，免费 AI 课程走一波

赛制安排

天池“挑战 baseline”将长期开放各个比赛第一赛季评测，报名和参赛无时间限制，提供永久排行榜。

## 参赛报名

1. 报名成功后，选手下载数据，在本地调试算法，提交结果；
2. 提交后将进行实时评测；每天排行榜更新时间为 15:00 和 21:00，按照评测指标得分从高到低排序；排行榜将选择历史最优成绩进行展示；

## 参赛对象

大赛面向全社会开放，参赛对象不限，要求以个人形式参赛。

天池新人官方钉钉群，搜索右侧群号即可加入：21756314

## 大赛激励

问鼎奖 ： 颁发给连续 7 天排行榜排名第一的队伍（超越 Baseline 且排名第一），获得 200 天池积分及 3000 天池粮票 （同次不重复计算，积分上限 500 天池积分）
极客奖 ： 启动 6 个月后，凡超越 Baseline 且排行榜入围 Top50 的选手可入围天池高端人才库，有机会获得天池工作机会的终面绿色通道
论文激励 ： 鼓励天池选手基于赛题发表论文，论文发表后，第一作者跟根据不同论文等级获得不同的天池奖品及相应的天池积分（解释权归主委会）

## 主办方

阿里云计算有限公司

# 任务说明：赛题与数据

## 竞赛题目

对于一条原创博文而言,转发、评论、赞等互动行为能够体现出用户对于博文内容的兴趣程度，也是对博文进行分发控制的重要参考指标。本届赛题的任务就是根据抽样用户的原创博文在发表一天后的转发、评论、赞总数，建立博文的互动模型，并预测用户后续博文在发表一天后的互动情况。

## 数据说明

## 第一赛季数据

### 训练数据（weibo_train_data(new)）

2015-02-01 至 2015-07-31  
博文的全部信息都映射为一行数据。其中对用户做了一定抽样，获取了抽样用户半年的原创博文，对用户标记和博文标记做了加密 发博时间精确到天级别。

| 字段          | 字段说明               | 提取说明      |
| ------------- | ---------------------- | ------------- |
| uid           | 用户标记               | 抽样&字段加密 |
| mid           | 博文标记               | 抽样&字段加密 |
| time          | 发博时间               | 精确到天      |
| forward_count | 博文发表一周后的转发数 |
| comment_count | 博文发表一周后的评论数 |
| like_count    | 博文发表一周后的赞数   |
| content       | 博文内容               |

### 预测数据（weibo_predict_data(new)）

2015-08-01 至 2015-08-31

| 字段    | 字段说明 | 提取说明      |
| ------- | -------- | ------------- |
| uid     | 用户标记 | 抽样&字段加密 |
| mid     | 博文标记 | 抽样&字段加密 |
| time    | 发博时间 | 精确到天      |
| content | 博文内容 |

### 选手需要提交的数据（weibo_result_data）

选手对预测数据（weibo_predict_data）中每条博文一周后的转、评、赞值进行预测

| 字段          | 字段说明               | 提取说明      |
| ------------- | ---------------------- | ------------- |
| uid           | 用户标记               | 抽样&字段加密 |
| mid           | 博文标记               | 抽样&字段加密 |
| forward_count | 博文发表一周后的转发数 |
| comment_count | 博文发表一周后的评论数 |
| like_count    | 博文发表一周后的赞数   |

选手提交结果文件的转、评、赞值必须为整数不接受浮点数！

注意：提交格式(.txt)：uid、mid、forward_count 字段以 tab 键分隔，forward_count、comment_count、like_count 字段间以逗号分隔

## 初赛评估指标

我们希望参赛队对于每一条博文预测出发表一周后的转发数、评论数和赞的数目，对于每一项均和真实值计算偏差：  
![img](https://img.alicdn.com/tps/TB1MIx6JVXXXXXhXVXXXXXXXXXX-633-495.png)
