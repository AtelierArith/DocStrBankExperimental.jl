```
with_span(f, name::String, [tracer=Tracer()]; kw...)
```

Call function `f` with the current span set a newly created one of `name` with `tracer`.

# Keyword arguments

  * `end_on_exit=true`, controls whether to call [`end_span!`](@ref) after `f` or not.
  * `record_exception=true`, controls whether to record the exception.
  * `set_status_on_exception=true`, decides whether to set status to [`SPAN_STATUS_ERROR`](@ref) automatically when an exception is caught.
  * The rest keyword arguments are forwarded to [`create_span`](@ref).
