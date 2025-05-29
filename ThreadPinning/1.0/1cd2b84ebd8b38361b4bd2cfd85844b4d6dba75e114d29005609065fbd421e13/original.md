```
unpinthread(; threadid::Integer = Threads.threadid())
```

Unpins the given Julia thread by setting the affinity mask to all unity. Afterwards, the OS is free to move the Julia thread from one CPU thread to another.
