```
find_route(m::MapData, node0::Int, node1::Int, node2::Int,
                    weights::SparseArrays.SparseMatrixCSC{Float64,Int64};
                    routing::Symbol = :astar, heuristic::Function = (u,v) -> zero(Float64),
                    get_distance::Bool = false, get_time::Bool = false)
```

3つのポイント（`node0`、`node1`、`node2`）を指定された重みで接続するルートを見つける
