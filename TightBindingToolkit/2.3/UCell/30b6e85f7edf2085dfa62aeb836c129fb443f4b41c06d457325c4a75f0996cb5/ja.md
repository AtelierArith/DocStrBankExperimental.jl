```julia
GetDistance(uc::UnitCell, base::Int64, target::Int64, offset::Vector{Int64}) --> Float64
```

位置 (0, `base`) と (R, `target`) の間の距離を取得します。ここで R = `offset` であり、単位セルの原始ベクトルの単位で表記されます。
