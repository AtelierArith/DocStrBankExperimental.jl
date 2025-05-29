```
unpinthreads(; threadpool::Symbol = :default)
```

Unpins all Julia threads by setting the affinity mask of all threads to all unity. Afterwards, the OS is free to move any Julia thread from one CPU thread to another.
