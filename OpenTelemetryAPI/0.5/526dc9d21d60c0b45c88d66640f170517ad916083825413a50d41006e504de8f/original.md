```
span_context([s::AbstractSpan])
```

Get the [`SpanContext`](@ref) from a span `s`. If `s` is not specified, [`current_span()`](@ref) will be used. `nothing` is returned if no span context found.
