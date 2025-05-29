```
task_done!(consume_ctx::AbstractConsumeContext, chunking_ctx::ChunkingContext)
```

Decrement the expected number of remaining work units by one. Called after each `consume!` call.

The this function should be called `ntasks` times where `ntasks` comes from the corresponding `setup_tasks!` call.

See also [`consume!`](@ref), [`setup_tasks!`](@ref), [`cleanup`](@ref)
