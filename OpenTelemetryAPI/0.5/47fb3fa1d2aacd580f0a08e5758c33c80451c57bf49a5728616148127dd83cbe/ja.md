```
with_span(f, s::AbstractSpan; kw...)
```

関数 `f` を提供されたスパン `s` で呼び出します。

# キーワード引数

  * `end_on_exit=true`、`f` の後に [`end_span!`](@ref) を呼び出すかどうかを制御します。
  * `record_exception=true`、例外を記録するかどうかを制御します。
  * `set_status_on_exception=true`、例外がキャッチされたときに自動的にステータスを [`SPAN_STATUS_ERROR`](@ref) に設定するかどうかを決定します。
