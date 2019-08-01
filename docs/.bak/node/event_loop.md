# Event-Loop

## 线程模型，为什么是单线程？

javascript是单线程的，此时是否有疑问为什么是单线程呢？多线程处理效率不是更高吗？需要从浏览器说起，在浏览器环境中对于DOM的操作，试想如果多个线程来对同一个DOM操作是不是就乱了呢，那也就意味着对于DOM的操作只能是单线程，避免DOM渲染冲突。另外，在浏览器环境中UI渲染线程和JS执行引擎是互斥的，一方在执行时都会导致另一方被挂起。

上面说了既然javascript是单线程的，那么同一时间只能处理一件事情，对于高并发大量请求不是会造成程序阻塞吗？有解决方案吗？答案是no，不会造成程序阻塞的解决方案是异步，异步的具体实现就是今天要讲的重点Event-Loop。

## 什么是EventLoop

EventLoop是Javascript实现异步的具体实现，在程序执行过程中，同步代码直接执行，异步代码／函数会先放在异步队列中，待同步的任务执行完成之后，轮询执行异步队列中的任务。

## 几种轮询技术

* read

* select

* poll

* epoll

如果是在面试中，如果问到轮询技术的实现一般也会考察select和epoll的区别


## 参考

* [The Node.js Event Loop, Timers, and process.nextTick()](https://github.com/nodejs/node/blob/v6.x/doc/topics/event-loop-timers-and-nexttick.md)
* [Node.js Event Loop 的理解 Timers，process.nextTick()](https://cnodejs.org/topic/57d68794cb6f605d360105bf)
* [什么是浏览器的事件循环（Event Loop）](https://segmentfault.com/a/1190000010622146)
