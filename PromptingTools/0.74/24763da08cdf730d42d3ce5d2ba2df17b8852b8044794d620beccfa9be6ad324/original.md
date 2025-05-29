```
aigenerate(tracer_schema::AbstractTracerSchema, prompt::ALLOWED_PROMPT_TYPE;
    tracer_kwargs = NamedTuple(), model = "", return_all::Bool = false, kwargs...)
```

Wraps the normal `aigenerate` call in a tracing/callback system. Use `tracer_kwargs` to provide any information necessary to the tracer/callback system only (eg, `parent_id`, `thread_id`, `run_id`).

Logic:

  * calls `initialize_tracer`
  * calls `aigenerate` (with the `tracer_schema.schema`)
  * calls `finalize_tracer`

# Example

```julia
wrap_schema = PT.TracerSchema(PT.OpenAISchema())
msg = aigenerate(wrap_schema, "Say hi!"; model = "gpt4t")
msg isa TracerMessage # true
msg.content # access content like if it was the message
PT.pprint(msg) # pretty-print the message
```

It works on a vector of messages and converts only the non-tracer ones, eg,

```julia
wrap_schema = PT.TracerSchema(PT.OpenAISchema())
conv = aigenerate(wrap_schema, "Say hi!"; model = "gpt4t", return_all = true)
all(PT.istracermessage, conv) #true
```
