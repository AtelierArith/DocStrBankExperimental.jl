```julia
inducevelocity(
    s::StaticArraysCore.SVector{2, AbstractArray},
    xeval
) -> Any

```

単位強度の渦フィラメントのセグメント `s` によって評価点 `xeval` で誘導される速度を計算します。セグメントの両方の頂点が無限の座標を持つ場合（同じ方向である必要があります）、無限でない座標は2つの頂点で平均化され、`xeval` からセグメントまでの距離が計算されます。
