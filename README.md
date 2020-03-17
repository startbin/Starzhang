# Starzhang
![](https://i.imgur.com/cEjAJjU.png)


|:dollar:Java面试题 |
|:dollar:Java集合 |
|:dollar:设计模式 |

|[Java面试题](https://juejin.im/post/5c4c4da051882525dd593a5b) |
|[Java集合](https://segmentfault.com/a/1190000021039973)|
|[设计模式](https://www.zhihu.com/people/zhang-bin-13-21/posts)|




| 🍏 | 🍱 |🥑  |
| :--------: | :---------:| :--------: |
| [JAVA基础](#JAVA基础) | [数据库](#数据库知识)|[多线程](#多线程) |  [算法](#算法)| 

| Java高级|
|-----|
| [Java NIO](https://blog.csdn.net/u011676417/article/details/86761750) |

### JAVA基础
- [面向对象继承](https://blog.csdn.net/u011676417/article/details/86601781)
- [面向对象接口多态](https://blog.csdn.net/u011676417/article/details/86602926)
- [集合 Map、可变参数、Collections](https://blog.csdn.net/u011676417/article/details/86370920)
- [IO File、递归](https://my.oschina.net/u/2441327/blog/3000695)
- [多线程【Thread、线程创建】](https://blog.csdn.net/u011676417/article/details/86500608)
- [XML](https://blog.csdn.net/u011676417/article/details/86532977)
- [网络编程【Socket网络编程】](https://blog.csdn.net/u011676417/article/details/86517114)

### 算法LeetCode刷题
- [两数之和](https://segmentfault.com/a/1190000019548980)
- [判断字符串是否有效](https://segmentfault.com/a/1190000019889890)

### 剑指offer刷题
- [数组查找、替换空格、从尾到头打印链表、重建二叉树、两个栈实现队列、旋转数组最小数字、斐波那契数列](https://my.oschina.net/u/2441327/blog/3188674)


### 数据库
- [数据库篇一](https://blog.csdn.net/u011676417/article/details/86558627)
- [数据库篇多表操作](https://blog.csdn.net/u011676417/article/details/86558635)
- [SQL语句查询](https://blog.csdn.net/u011676417/article/details/86568017)
- [多表查询](https://blog.csdn.net/u011676417/article/details/86586892)
- [操作数据库表](https://blog.csdn.net/u011676417/article/details/86614484)
- [JDBC](https://yq.aliyun.com/articles/691266)


### 多线程
- [线程池](https://blog.csdn.net/u011676417/article/details/80762529)


### Java面试
[Java面试](https://juejin.im/post/5c4c4da051882525dd593a5b)


### 容器
- [容器](https://my.oschina.net/u/2441327/blog/3007519)

<!-- TOC -->
- [JVM内存布局](#JVM-内存布局)
<!-- /TOC -->
### JVM 虚拟机
   JVM中将内存分为若干部分：堆、方法区、虚拟机栈、本地方法栈、程序计数器
   
**线程私有的：**

- 程序计数器
- 虚拟机栈
- 本地方法栈

**线程共享的：**

- 堆
- 方法区
- 直接内存 (非运行时数据区的一部分)

### 程序计数器

 程序计数器：该区域是内存中较小的一块区域---是当前线程在执行的字节码的行号指示器。程序计数器是线程私有的，每个线程都有一个程序计数器，线程之间的程序计数器相互独立，互不干扰。是java虚拟机规范中唯一一个没有规定任何OutOfMemoryError情况的区域

### 虚拟机栈

是线程私有的，其生命周期与线程是相同的。虚拟机栈描述的是java方法执行的内存模型，每个方法在执行的时都会创建一个栈帧用于存储局部变量表，操作数栈、动态链接、方法出口等信息。每个方法从调用到结束就会有栈帧在虚拟机栈中入栈和出栈。一个方法的调用链可能会很长，于是当调用一个方法时，可能会有很多的方法都处于执行状态,但是对于执行引擎来讲，至于位于虚拟机栈栈顶的栈帧才是有效的，这个栈帧被称为当前栈，这个栈帧所关联的方法被称为当前方法，执行引擎的所有指令都是针对当前栈帧进行操作的。Stackoverflowerror异常（当线程申请的栈空间大于虚拟机所允许的深度时）；outfmemoryError：当虚拟机栈无法申请到足够内存时。局部变量表是一组变量值的存储空间，局部变量表的存储单位是slot。若为实例方法，则第0个slot是存储的指向所有实例对象的引用，在方法中可以通过this来访问到这个隐含的参数；往下是参数，再往下是方法内的局部变量。对于操作数栈，在方法刚开始执行时操作数栈为空，执行过程中会有各种字节码指令写入或者谈出。比如算法运算或者调用其他方法时的参数等。动态链接：类似于与静态链接即解析时符号引用转化为直接引用，动态链接是指在运行时转化为直接引用。

###  本地方法栈:

功能与虚拟机栈相同，只不过本地方法栈是为native方法服务

### 堆

java堆是被线程共享的一块区域。Java堆是用来存放实例对象以及数组对象。由于现在有了逃逸分析技术，也可以将对象分配在栈上。同时java堆也是垃圾回收的主要区域，垃圾回收主要采用分代回收，有年轻代，老年代。Java堆可以是物理上不连续的区域，只要逻辑上连续即可。在堆中为对象分配内存的分配方法有：碰撞指针（前提绝对规整，注意多线程同步问题，采用CAS原理加失败重试实现或者本地线程分配缓冲）和空闲列表（不是规整的内存）方法，选择哪一种分配方法取决于是否规整，是否规整取决于采用的垃圾回收算法是否压缩。对象的访问一般有两种方式：句柄和直接访问。堆空间不足时抛出outOfMemoryError。

在 JDK 7 版本及JDK 7 版本之前，堆内存被通常被分为下面三部分：

1. 新生代内存(Young Generation)
2. 老生代(Old Generation)
3. 永生代(Permanent Generation)

![JVM堆内存结构-JDK7](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-11/JVM堆内存结构-JDK7.jpg)


JDK 8 版本之后方法区（HotSpot 的永久代）被彻底移除了（JDK1.7 就已经开始了），取而代之是元空间，元空间使用的是直接内存。

![JVM堆内存结构-JDK8](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-11/JVM堆内存结构-jdk8.jpg)

**上图所示的 Eden 区、两个 Survivor 区都属于新生代（为了区分，这两个 Survivor 区域按照顺序被命名为 from 和 to），中间一层属于老年代。**

### 方法区

与堆一样，是线程共享的的区域。用于存储已经被虚拟机加载的类的类信息、常量、静态变量、编译后的代码，运行时常量池（存储编译器生成的各种字面量与符号引用）等。方法区中有一个运行时常量池，class文件中的常量池在类被加载后就被放入运行时常量池。运行时常量池相对于class文件中的常量池，具有动态性。可以在运行期间通过intern将常量放入池中，方法区空间不足时抛出outOfMemoryError。


在java虚拟机的规范之外还存在一个堆外内存，即直接内存。堆外内存能减少IO时的内存复制，实现零拷贝，不需要堆内存Buffer拷贝一份到直接内存，然后才写入Socket中；而且也没GC。
		 
		 优点：1、减少了垃圾回收的工作，因为垃圾回收会暂停其他的工作（可能使用多线程或者时间片的方式，根本感觉不到）
		      2、加快了复制的速度。因为堆内在flush到远程时，会先复制到直接内存（非堆内存），然后在发送，而堆外内存相当于省略掉了这个工作。
				
		 缺点：1、堆外内存难以控制，如果内存泄漏，那么很难排查
		      2、堆外内存相对来说，不适合存储很复杂的对象。一般简单的对象或者扁平化的比较适合。
