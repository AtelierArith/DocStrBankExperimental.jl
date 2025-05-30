```
isright(::Const) = false
isright(::Identity) = true
```

[`isidentity`](@ref) と同じですが、`Either` を扱う際に読みやすいかもしれません。
