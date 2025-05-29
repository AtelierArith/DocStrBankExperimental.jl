```
SpanStatus(code, description=nothing)
```

Possible codes are:

  * `SPAN_STATUS_UNSET`
  * `SPAN_STATUS_ERROR`
  * `SPAN_STATUS_OK`

`description` is required when `code` is `SPAN_STATUS_ERROR`.
