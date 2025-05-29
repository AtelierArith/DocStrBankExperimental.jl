```
struct Level{L, S, T<:Union{Real, AbstractQuantity{<:Real}}} <: LogScaled{L}
```

対数スケールに基づくレベル。対数スケールに関する詳細は `L <: LogInfo` にエンコードされています。`S` はレベルの参照量であり、型ではありません。この型には1つのフィールド `val::T` があり、比 `val/S` の対数が取られます。この型は [`Unitful.Gain`](@ref) と異なり、`val` は線形量です。
