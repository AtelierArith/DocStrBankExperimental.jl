```
Spline{P<:CurveType,S<:Number,N,M}
```

`M` は曲線の次数、すなわちパラメータ変数 u の最高次の幂です。`P` は [`CurveType`](@ref) を決定します。

すべてのスプラインタイプは以下を実装しなければなりません：

```julia
point(curve,u)
```

およびフィールド `controlpolygon` を持つ必要があります。
