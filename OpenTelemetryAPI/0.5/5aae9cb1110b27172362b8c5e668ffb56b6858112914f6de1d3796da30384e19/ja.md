```
SpanStatus(code, description=nothing)
```

可能なコードは次のとおりです：

  * `SPAN_STATUS_UNSET`
  * `SPAN_STATUS_ERROR`
  * `SPAN_STATUS_OK`

`description` は `code` が `SPAN_STATUS_ERROR` の場合に必要です。
