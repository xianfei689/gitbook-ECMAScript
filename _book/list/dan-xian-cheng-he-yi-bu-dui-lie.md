# 单线程和异步队列

setTimeout和setInterval是JS内置的两个定时器，使用很简单，但这两个方法背后的原理却不简单。

我们知道，JS是**单线程语言**，在浏览器中，当JS代码被加载时，浏览器会为其**分配一个主线程**来执行任务\(函数\)，主线程会形成一个**全局执行环境**，执行环境采用**栈的方式将待执行任务按顺序依次来执行**。

但在浏览器中有一些任务是非常耗时的，比如http请求、定时器、事件回调等，为了保证其他任务的执行效率不被影响，**JS在执行环境中维护了一个异步队列\(也叫工作线程\)，并将这些任务放入队列中进行等待，这些任务的执行时机并不确定，只有当主线程的任务执行完成以后，才会去检查异步队列中的任务是否需要开始执行。**这就是为什么setTimeout\(fn,0\) 始终要等到最后执行的原因。

