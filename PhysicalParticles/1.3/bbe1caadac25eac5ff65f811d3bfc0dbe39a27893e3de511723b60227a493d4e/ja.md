```
ZeroValue(::Type{T}, ::Nothing) where T<:Number
ZeroValue(::Type{T}, units::Vector{Unitful.FreeUnits{N, D, nothing} where D where N} = uAstro) where T<:Number

型 `T` のゼロ値を対応する `units` で提供する不変構造体を構築します（デフォルトは `uAstro` です）。単位がない場合は `nothing` を使用します。累積和、配列の初期化などに便利です。

# 例

```

jl ZeroValue(Float32, nothing) ZeroValue(Int32) ZeroValue(BigFloat, uSI) ZeroValue(Measurement, uCGS) ```
