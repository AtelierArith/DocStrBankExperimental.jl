```julia
eachring(
    Grid::Type{<:SpeedyWeather.RingGrids.AbstractGridArray},
    nlat_half::Integer
) -> Any

```

与えられたグリッドのリング `j` のすべての経度点の開始と終了のリングインデックス `i0:i1` を、解像度 `nlat_half` で計算します。グリッドのリングをループするために使用されます。これらのインデックスは、すべての `grid.rings` にも事前に計算されています。
