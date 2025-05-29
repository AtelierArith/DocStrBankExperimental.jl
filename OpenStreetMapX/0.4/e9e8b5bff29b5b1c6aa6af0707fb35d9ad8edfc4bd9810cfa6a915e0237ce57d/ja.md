```
find_optimal_waypoint_exact(m::MapData, weights::SparseArrays.SparseMatrixCSC{Float64,Int64}, node0::Int, node1::Int, waypoints::Dict{Int,Int})
```

ルートを最小化するウェイポイントを見つけます。正確な解を返します。
