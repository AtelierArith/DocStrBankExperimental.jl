```
nameof_string(::Type{T})
nameof_string(T::Module)
nameof_string(::T) where {T}
```

`T`の安定した名前を取得します。これは、[`StableHashTraits.transform_type`](@ref)および[`StableHashTraits.transform_type_value`](@ref)の独自のメソッドを書くための便利なユーティリティです。安定した名前は`nameof`から計算されます。匿名の名前（例：`module_nameof_string(x -> x+1)`）はエラーをスローします。なぜなら、この場合、安定した名前を取得することができないからです。
