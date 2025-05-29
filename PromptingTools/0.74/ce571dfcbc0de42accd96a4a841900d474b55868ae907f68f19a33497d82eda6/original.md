```
aiimage(tracer_schema::AbstractTracerSchema, prompt::ALLOWED_PROMPT_TYPE;
    tracer_kwargs = NamedTuple(), model = "", kwargs...)
```

Wraps the normal `aiimage` call in a tracing/callback system. Use `tracer_kwargs` to provide any information necessary to the tracer/callback system only (eg, `parent_id`, `thread_id`, `run_id`).

Logic:

  * calls `initialize_tracer`
  * calls `aiimage` (with the `tracer_schema.schema`)
  * calls `finalize_tracer`
