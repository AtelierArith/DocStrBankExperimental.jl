```
getaffinity(; threadid = Threads.threadid(), cutoff = cpuidlimit())
```

Get the thread affinity of a Julia thread. Returns the affinity mask as a vector of zeros and ones. By default, the mask is cut off at `Sys.CPU_THREADS`. This can be tuned via the `cutoff` keyword argument (`nothing` means no cutoff).
