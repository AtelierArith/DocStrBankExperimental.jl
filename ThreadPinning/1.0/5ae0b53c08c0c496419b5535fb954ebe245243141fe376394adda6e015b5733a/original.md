```
mpi_pinthreads(symbol; compact, kwargs...)
```

Pin the Julia threads of MPI ranks in a round-robin fashion to specific domains (e.g. sockets). Supported domains (`symbol`) are `:sockets`, `:numa`, and `:cores`.

When calling this function on all MPI ranks, the Julia threads of the latter will be distributed in a round-robin fashion among the specified domains and will be pinned to non-overlapping ranges of CPU-threads within the domains.

A multi-node setup, where MPI ranks are hosted on different nodes, is supported.

If `compact=false` (default), physical cores are occupied before hyperthreads. Otherwise, CPU-cores - with potentially multiple CPU-threads - are filled up one after another (compact pinning).

*Example:*

```
using ThreadPinning
using MPI
MPI.Init()
mpi_pinthreads(:sockets)
```
