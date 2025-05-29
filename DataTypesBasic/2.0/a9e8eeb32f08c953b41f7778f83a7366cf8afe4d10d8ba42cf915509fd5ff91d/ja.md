```
isoption(::Const{Nothing}) = true
isoption(::Identity) = true
isoption(other) = false
```

何かが[`Option`](@ref)であるかどうかを確認します。
