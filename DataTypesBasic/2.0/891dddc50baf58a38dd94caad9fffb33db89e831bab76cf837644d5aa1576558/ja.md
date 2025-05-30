```
iseither(::Const) = true
iseither(::Identity) = true
iseither(other) = false
```

何かが[`Either`](@ref)であるかどうかを確認します。
