```
distance(M::AbstractPowerManifold, p, q, r::Real=2)
distance(M::AbstractPowerManifold, p, q, m::AbstractInverseRetractionMethod=LogarithmicInverseRetraction(), r::Real=2)
```

`q`と`p`の間の距離を[`AbstractPowerManifold`](@ref)上で計算します。

まず、成分ごとの距離は`M.manifold`上のリーマン距離関数を使用して計算されます。これらは[`AbstractInverseRetractionMethod`](@ref) `m`の`norm`を使用して近似できます。これにより、距離値の配列が得られます。

次に、この距離の配列に対して`r`-ノルムを計算します。これは`r`が使用される唯一の場所でもあります。
