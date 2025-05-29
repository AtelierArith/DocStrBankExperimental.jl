```
OrbitStateVector(t::Tepoch, r::AbstractVector{Tr}, v::AbstractVector{Tv}[, a::AbstractVector{Ta}])
```

エポック `t` [ユリウス日]、位置 `r` [m]、速度 `v` [m / s]、および加速度 `a` [m / s²] を持つ軌道状態ベクトルを作成します。後者が省略された場合、`[0, 0, 0]` で埋められます。

オブジェクトの型は `Tr`、`Tv`、および `Ta` を昇格させることによって得られます。
