```
distributed_pinthreads(symbol;
    include_master = false,
    compact = false,
    nthreads_per_proc = Threads.nthreads(),
    kwargs...)
```

Pin the Julia threads of Julia workers in a round-robin fashion to specific domains (e.g. sockets). Supported domains (`symbol`) are `:sockets`, `:numa`, and `:cores`.

When calling this function, the Julia threads of all Julia workers will be distributed in a round-robin fashion among the specified domains and will be pinned to non-overlapping ranges of CPU-threads within the domains.

A multi-node setup, where Julia workers are hosted on different nodes, is supported.

If `include_master=true`, the master process (`Distributed.myid() == 1`) will be pinned as well.

If `compact=false` (default), physical cores are occupied before hyperthreads. Otherwise, CPU-cores - with potentially multiple CPU-threads - are filled up one after another (compact pinning).

*Example:*

```
using Distributed
addprocs(3)
@everywhere using ThreadPinning
distributed_pinthreads(:sockets)
```
