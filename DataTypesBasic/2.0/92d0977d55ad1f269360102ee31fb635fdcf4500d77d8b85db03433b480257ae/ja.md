```
issuccess(::Identity) = true
issuccess(::Const{<:Exception}) = false
```

[`isright`](@ref) と似ていますが、`Const{<:Exception}` にのみ定義されています。他の `Const` に適用すると MethodError が発生します。
