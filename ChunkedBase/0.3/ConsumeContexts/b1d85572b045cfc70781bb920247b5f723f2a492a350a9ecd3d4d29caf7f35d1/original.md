```
cleanup(consume_ctx::AbstractConsumeContext, e::Exception)
```

You can override this method do custom exception handling with your consume context. This method is called immediately before a `rethrow()` which forwards the `e` further.

See also [`consume!`](@ref), [`setup_tasks!`](@ref), [`task_done!`](@ref), [`sync_tasks`](@ref)
