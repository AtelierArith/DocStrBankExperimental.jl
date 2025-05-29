```
isfailure(::Identity) = false
isfailure(::Const{<:Exception}) = true
```

[`isleft`](@ref)と似ていますが、`Const{<:Exception}`にのみ定義されています。他の`Const`に適用するとMethodErrorが発生します。
