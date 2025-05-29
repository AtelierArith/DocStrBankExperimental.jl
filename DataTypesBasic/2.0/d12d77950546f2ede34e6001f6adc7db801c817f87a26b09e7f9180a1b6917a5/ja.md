```
isright(::Const) = false
isright(::Identity) = true
```

[`isidentity`](@ref) と同じですが、`Either` を扱うときに読みやすいかもしれません。
