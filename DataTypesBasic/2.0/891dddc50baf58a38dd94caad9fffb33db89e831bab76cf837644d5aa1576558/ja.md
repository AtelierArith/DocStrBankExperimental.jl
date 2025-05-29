```
iseither(::Const) = true
iseither(::Identity) = true
iseither(other) = false
```

[`Either`](@ref) が何かであるかを確認します。
