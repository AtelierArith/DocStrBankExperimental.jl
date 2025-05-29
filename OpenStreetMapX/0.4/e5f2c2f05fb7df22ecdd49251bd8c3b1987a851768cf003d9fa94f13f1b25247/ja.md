```
fastest_route(m::MapData, node1::Int, node2::Int, node3::Int;
                    routing::Symbol = :astar,
                    speeds::Dict{Int,Float64}=SPEED_ROADS_URBAN)
```

マップ `m` 上で `node1` と `node2` および `node3` の間の最速ルートを見つけ、道路クラスに対する `speeds` を仮定します。
