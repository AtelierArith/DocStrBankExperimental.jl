```
span_context([s::AbstractSpan])
```

スパン `s` から [`SpanContext`](@ref) を取得します。`s` が指定されていない場合は、[`current_span()`](@ref) が使用されます。スパンコンテキストが見つからない場合は `nothing` が返されます。
