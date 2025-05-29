```
find_optimal_waypoint_approx(m::MapData, weights::SparseArrays.SparseMatrixCSC{Float64,Int64}, node0::Int, node1::Int, waypoints::Dict{Int,Int})
```

Find waypoint minimizing the route. Returns an approximate solution.
