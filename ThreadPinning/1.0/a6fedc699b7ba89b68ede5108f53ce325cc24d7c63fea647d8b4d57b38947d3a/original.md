```
printaffinity(; threadid::Integer = Threads.threadid())
```

Print the affinity mask of the Julia thread.

The keyword argument `groupby` may be used to change how CPU-threads are grouped visually. It defaults to `groupby=:socket`. Other valid values are `:numa` and `:core`.
