```
isleft(::Const) = true
isleft(::Identity) = false
```

[`isconst`](@ref)と同じですが、`Either`を扱うときに読みやすいかもしれません。
