```
ensure_procinit(pid::Int)
ensure_procinit(pids::AbstractVector{Int} = workers())
```

Run process initialization code on the given process(es) if necessary, returns after initialization is complete.

When using a [`FlexWorkerPool`](@ref), worker initialization can safely be run in the background though, as the pool will only offer workers (via `take!(pool)`) after it has fully initialized them.

See also [`ParallelProcessingTools.get_procinit_code`](@ref) and [`ParallelProcessingTools.add_procinit_code`](@ref).

See also [`ParallelProcessingTools.get_procinit_code`](@ref), [`ParallelProcessingTools.ensure_procinit`](@ref), [`ParallelProcessingTools.global_procinit_level`](@ref) and [`ParallelProcessingTools.current_procinit_level`](@ref).
