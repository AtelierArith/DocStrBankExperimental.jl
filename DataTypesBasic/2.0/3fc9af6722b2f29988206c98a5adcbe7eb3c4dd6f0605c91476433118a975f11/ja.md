```
isoption(::Const{Nothing}) = true
isoption(::Identity) = true
isoption(other) = false
```

何かが[`Try`](@ref)であるかどうかを確認します。
