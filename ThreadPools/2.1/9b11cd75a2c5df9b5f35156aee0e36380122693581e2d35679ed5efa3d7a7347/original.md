```
ThreadPools.showactivity([io, ]log, dt, t0=0, t1=Inf; nthreads=Threads.nthreads())
```

Produces a textual graph of the thread activity in the provided log.

The format of the output is

```julia
julia> ThreadPools.showactivity("mylog.txt", 0.1)
0.000   -   -   -   -
0.100   4   2   1   3
0.200   4   2   5   3
0.300   4   6   5   3
0.400   4   6   5   7
0.500   8   6   5   7
0.600   8   6   5   7
0.700   8   6   -   7
0.800   8   6   -   7
0.900   8   -   -   7
1.000   8   -   -   7
1.100   8   -   -   -
1.200   8   -   -   -
1.300   -   -   -   -
1.400   -   -   -   -
```

where the first column is time, and each column afterwards is the active job id in each thread (threads 1:nthreads, left to right) at that point in time.

If `io` is provided, the output will be written there.  `log` may be a log IO  object, or a filename to be opened and read.  `dt` is the time step for each row, `t0` is the optional starting time, `t1` the optional stopping  time, and `nthreads` is the number of threads to print.
