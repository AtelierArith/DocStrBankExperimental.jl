```
consume!(consume_ctx::AbstractConsumeContext, payload::ParsedPayload{<:AbstractResultBuffer, <:AbstractParsingContext})
```

Override with your `AbstractConsumeContext` to provide a custom logic for processing the parsed results in `AbstractResultBuffer`. The method is called from multiple tasks in parallel, just after each corresponding `task_buf` has been populated. `task_buf` is only filled once per chunk and is only accessed by one task at a time.

See also [`consume!`](@ref), [`setup_tasks!`](@ref), [`setup_tasks!`](@ref), [`cleanup`](@ref), [`AbstractResultBuffer`](@ref)
