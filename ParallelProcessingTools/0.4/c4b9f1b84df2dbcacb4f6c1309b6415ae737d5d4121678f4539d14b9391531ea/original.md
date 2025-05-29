```
runworkers(
    runmode::ParallelProcessingTools.RunProcsMode
    manager::Distributed.AbstractClusterManager = ppt_cluster_manager()
)
```

Run Julia worker processes.

By default ensures that all workers processes use the same Julia project environment as the current process (requires that file systems paths are consistenst across compute hosts).

The new workers are managed via [`ppt_cluster_manager()`](@ref) and automatically added to the [`ppt_worker_pool()`](@ref)

Returns a tuple `(task, n)`. Here, `task::Task` is done when all workers have terminated. `n` is either an `Integer`, if the number of workers that will be started is known, or `Nothing`, if the number of workers can't be predicted (accurately).

Example:

```julia
task, n = runworkers(OnLocalhost(n = 4))
```

See also [`worker_resources()`](@ref).
