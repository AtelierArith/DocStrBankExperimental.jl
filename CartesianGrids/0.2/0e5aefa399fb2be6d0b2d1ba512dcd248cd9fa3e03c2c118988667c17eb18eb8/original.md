```
optimize_gridsize(nx0,ny0[;region_size=4,optimize_threads=true,nthreads_max=length(cpu_info()),nsamp=1])
```

Given a nominal grid size (`nx0` x `ny0`), determine the optimal grid size that minimizes the compute time. Optional arguments are the `optimize_threads` flag and the maximum number of threads `nthreads_max` (if multithreading is allowed) and the number of samples to take of the cpu time for each trial. Returns optimal `nx`, `ny`, and the corresponding CPU time.
