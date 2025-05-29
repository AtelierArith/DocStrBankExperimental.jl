```
scaling_benchmark(; threads=1:Threads.nthreads(), kwargs...)
```

Runs a comprehensive STREAM benchmark for a varying number of threads (as indicated by `threads`). Returns a vector of the measured maximal memory_bandwidths (in MB/s) for each number of threads.
