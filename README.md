# 系统架构设计 System-Design 2021

## 新鲜事系统（News Feed System）

## 秒杀系统与订票系统（Seckill & Booking System）

## 优惠券系统（Coupons System）

### 核心流程

- **发券**
  - 发券的方式：同步发送 or 异步发送
- **领券**
  - 谁能领：所有用户 or 指定用户
  - 领取上限：一个优惠券最多能领取多少张
  - 领取方式：用户主动领取 or 系统被动发放
- **用券**
  - 作用方式：商品、商户、类目等
  - 计算方式：是否互斥、是否达到门槛等

### 需求拆解

- 商家侧
  - 创建优惠券
  - 发送优惠券
- 用户侧
  - 领取优惠券
  - 下单
  - 使用优惠券
  - 支付

### 优惠券系统难点

- 券的分布式事务，使用券的过程会出现分布式问题分析
- 如何防止超发
- 如何大批量给用户发圈
- 如何限制券的使用条件
- 如何防止用户重复领券

## 表单设计

- 1、券批次（券模板）
  - 指一批优惠券的抽象、模板，包含优惠券的大部分属性。
  - 例：商家创建了一批优惠券，共1000张，使用时间为2021-01-01 00:00:00 ~ 2021-01-31 2359:59
  - 规定只有化妆品类目商品才能使用，满100减50.
- 2、券
  - 发放到用户的一个实体，已与用户绑定；
  - 例：将某批次的优惠券中的一张发送给某个用户，此时优惠券属于用户。
- 3、规则
  - 优惠券的使用有规则和条件限制，比如满100减50券，需要达到门槛金额100元才能使用

![001](./images/001.png)

### 异步处理思想

特别大的请求里，先不要想着立马把这些请求处理掉，而是先把这些请求存下来，再从存储下来的浏览中，按照能够处理的速度一点点进行处理。

## 协同实时编辑系统（Collaboration Real-Time Editor System）

## 定位信息服务系统（Location Based Services System）
