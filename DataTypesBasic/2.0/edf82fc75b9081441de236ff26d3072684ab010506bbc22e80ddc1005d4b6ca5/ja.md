```
issome(::Identity) = true
issome(::Const{Nothing}) = false
```

[`isright`](@ref)と似ていますが、`Const{Nothing}`にのみ定義されています。他の`Const`に適用するとMethodErrorが発生します。
