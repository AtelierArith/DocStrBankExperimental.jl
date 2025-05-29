```
fastest_route(m::MapData, node1::Int, node2::Int;
                    routing::Symbol = :astar,
                    speeds::Dict{Int,Float64}=SPEED_ROADS_URBAN)
```

マップ `m` 上で `node1` と `node2` の間の最速ルートを見つけます。道路クラスのための `speeds` を仮定します。
