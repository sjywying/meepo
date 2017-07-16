Meepo是一个轻量级的数据迁移工具，主要针对Mysql、ParquetFile之间的数据交换场景。

当然也定制了一些扩展，比如Redis、ElasticSearch等。

Meepo主要是用来解决如下几个问题：

1、Mysql表的同步，持续读取原表的新增数据，写入一个定制化的新表，有一些简单的数据加工。

这个需求也有很多公司是基于otter、cannal来做的，meepo和datax原理差不多，基于JDBC。

2、快速复制一张Mysql表，以最快的速度完成一个镜像的拷贝，可适当取舍列，主要用于测试需求。

为了快速写入Mysql，Meepo还是做了很多细致的性能优化工作的，基本上可以满足绝大多数需求了。

3、将在线库的数据生成Parquet，并写入到HDFS上，或者生成本地文件，方便数据的传递。

跟Sqoop功能差不多，但是Sqoop基于Yarn的MR不太好控制，而且依赖有些重。

4、两张Mysql表的比对，目前只能针对主键ID，进行差异比较，找到丢失的数据行。

主要是基于Bitmap，在有限的内存空间里，快速比对数据差异。

5、基于Plugin的定制开发，Meepo默认提供了一些Plugin，也允许plugin组合使用和自定义。

默认提供的插件能自动处理字段类型的差异，能够完成简单的Join计算。
