```
aiembed(tracer_schema::AbstractTracerSchema,
    doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}}, postprocess::Function = identity;
    tracer_kwargs = NamedTuple(), model = "", kwargs...)
```

Wraps the normal `aiembed` call in a tracing/callback system. Use `tracer_kwargs` to provide any information necessary to the tracer/callback system only (eg, `parent_id`, `thread_id`, `run_id`).

Logic:

  * calls `initialize_tracer`
  * calls `aiembed` (with the `tracer_schema.schema`)
  * calls `finalize_tracer`
