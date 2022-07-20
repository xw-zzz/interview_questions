# interview_questions

## 1.是否了解CAP理论？

- CAP定理: 指的是在一个分布式系统中，Consistency（一致性）、 Availability（可用性）、Partition tolerance（分区容错性），三者不可同时获得

  - 一致性（C）：所有节点都可以访问到最新的数据
  - 可用性（A）：每个请求都是可以得到响应的，不管请求是成功还是失败
  - 分区容错性（P）：除了全部整体网络故障，其他故障都不能导致整个系统不可用

- CAP理论就是说在分布式存储系统中，最多只能实现上面的两点。而由于当前的网络硬件肯定会出现延迟丢包等问题，所以分区容忍性是我们必须需要实现的。所以我们只能在一致性和可用性之间进行权衡。

  |                 | Nacos                      | Eureka | Consul            | Zookeeper  |
  | :-------------- | :------------------------- | :----- | :---------------- | ---------- |
  | 一致性协议      | CP+AP                      | AP     | CP                | CP         |
  | 健康检查        | TCP/HTTP/MYSQL/Client Beat | 心跳   | TCP/HTTP/gRPC/Cmd | Keep Alive |
  | 雪崩保护        | 有                         | 有     | 无                | 无         |
  | 访问协议        | HTTP/DNS                   | HTTP   | HTTP/DNS          | TCP        |
  | SpringCloud集成 | 支持                       | 支持   | 支持              | 支持       |