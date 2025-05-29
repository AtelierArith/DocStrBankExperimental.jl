```
span_status!([current_span()], code::SpanStatusCode, description=nothing)
```

Update the status of span `s` by following the original specification. `description` is only considered when the `code` is `SPAN_STATUS_ERROR`. Only valid when the span is not ended yet.
