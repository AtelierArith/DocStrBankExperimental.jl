```
distance(M::ProductManifold, p, q, r::Real=2)
distance(M::ProductManifold, p, q, m::AbstractInverseRetractionMethod=LogarithmicInverseRetraction(), r::Real=2)
```

`q`と`p`の間の距離を[`ProductManifold`](@ref)上で計算します。

まず、成分ごとの距離が計算されます。これらは[`AbstractInverseRetractionMethod`](@ref) `m`の`norm`を使用して近似できます。次に、これらの要素のタプルの`r`-ノルムが計算されます。
