```
FlexWorkerPool{WP<:AbstractWorkerPool}(
    worker_pids::AbstractVector{Int};
    label::AbstractString = "", maxoccupancy::Int = 1, init_workers::Bool = true
)::AbstractWorkerPool

FlexWorkerPool(; caching = false, withmyid::Bool = true, kwargs...)
```

An flexible worker pool, intended to work with cluster managers that may add and remove Julia processes dynamically.

If the current process (`Distributed.myid()`) is part of the pool, resp. if `withmyid` is `true`, it will be used as a fallback when no other workers are in are members of the pool (e.g. because no other processes have been added yet or because all other processes in the pool have terminated and been removed from it). The current process will *not* be used as a fallback when all other workers are currently in use.

If `caching` is true, the pool will use a `Distributed.CachingPool` as the underlying pool, otherwise a `Distributed.WorkerPool`.

If `maxoccupancy`is greater than one, individual workers can be used `maxoccupancy` times in parallel. So `take!(pool)` may return the same process ID `pid` multiple times without a `put!(pool, pid)` in between. Such a (ideally moderate) oversubscription can be useful to reduce latency-related idle times on workers: e.g. if communication latency to the worker is not short compared the the runtime of the function called on them. Or if the remote functions are often blocked waiting for I/O. Note: Workers still must be put back the same number of times they were taken from the pool, in total.

If `init_workers` is `true`, workers taken from the pool will be guaranteed to be initialized to the current global initialization level (see [`@always_everywhere`](@ref)).

`WP` is the type of the underlying worker pool used, e.g. `Distributed.WorkerPool` (default) or `Distributed.CachingPool`.

Example:

```julia
using ParallelProcessingTools, Distributed

pool = FlexWorkerPool(withmyid = true, maxoccupancy = 3)

workers(pool)

pids = [take!(pool) for _ in 1:3]
@assert pids == repeat([myid()], 3)
foreach(pid -> put!(pool, pid), pids)

addprocs(4)
worker_procs = workers()
push!.(Ref(pool), worker_procs)

pids = [take!(pool) for _ in 1:4*3]
@assert pids == repeat(worker_procs, 3)
foreach(pid -> put!(pool, pid), pids)
rmprocs(worker_procs)

pids = [take!(pool) for _ in 1:3]
@assert pids == repeat([myid()], 3)
foreach(pid -> put!(pool, pid), pids)
```
