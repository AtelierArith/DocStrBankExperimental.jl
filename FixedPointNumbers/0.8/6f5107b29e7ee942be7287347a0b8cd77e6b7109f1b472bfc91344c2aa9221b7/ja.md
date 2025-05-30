```
floattype(::Type{T})::Type{<:AbstractFloat}
```

整数オーバーフローなしで型 `T` のインスタンスで計算を行うのに適した最小限の型を返します。

`floattype(T)` のフォールバック定義は `T<:AbstractFloat` にのみ適用されます。ただし、`floattype` を拡張して `AbstractFloat` のサブタイプでない型を返すことは許可されています。重要な特徴は、返される型が整数オーバーフローなしで計算をサポートする必要があることです。

一般的に、返される型は入力型の全精度をエンコードするのに必要な最小ビット幅を持つべきですが、計算効率を優先する必要があります。そのため、`Float16` のような型は、ハードウェアサポートが保証されているシナリオを除いて避けるべきです。

# 例

古典的な使用法は、`FixedPoint` を `AbstractFloat` に昇格させてオーバーフロー動作を回避することです。

```jldoctest
julia> x = N0f8(1.0)
1.0N0f8

julia> x + x # overflow
0.996N0f8

julia> T = floattype(x)
Float32

julia> T(x) + T(x)
2.0f0
```

以下は、非 `AbstractFloat` に対する `floattype` の有効な拡張を示しています。

```julia
julia> using FixedPointNumbers, ColorTypes

julia> floattype(RGB{N0f8})
RGB{Float32}
```

`RGB` 自体は `AbstractFloat` のサブタイプではありませんが、`RGB{N0f8}` とは異なり、`RGB{Float32}` との演算は整数オーバーフローの影響を受けません。
