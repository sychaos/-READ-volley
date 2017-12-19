### Volley

概述
    调用链从 Volley.newRequestQueue开始 这个方法会初始化BasicNetwork，其实是个HttpClient或者HttpConnect(历史遗留问题不再赘述)，初始化后会调用
    RequestQueue.start 在这里会开启一个缓存线程，和四个（默认）网络线程，无论是缓存线程还是网络线程都会因为BlockingQueue.take为空而阻塞线程，
    然后通过调用RequestQueue.add将request加入缓存队列和网络队列
    然后就是 下没下载过啊，有木有缓存啊，缓存过没过期啊 恩。。。
    值得注意的是在网络线程中 对请求成功返回的数据 volley会直接缓存他的entry（并不支持断点续传） 大概也因为这个原因 volley并不适合数据量大的访问，但适合请求频繁的访问

Volley is an HTTP library that makes networking for Android apps easier and, most
importantly, faster.

For more information about Volley and how to use it, visit the [Android developer training
page](https://developer.android.com/training/volley/index.html).
