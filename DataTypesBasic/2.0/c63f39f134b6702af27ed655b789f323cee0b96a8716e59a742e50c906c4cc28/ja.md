```
isnone(::Identity) = false
isnone(::Const{Nothing}) = true
```

[`isleft`](@ref)と似ていますが、`Const{Nothing}`にのみ定義されています。他の`Const`に適用するとMethodErrorが発生します。
