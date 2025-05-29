```
fastest_route(m::MapData, node1::Int, node2::Int, node3::Int;
                    routing::Symbol = :astar,
                    speeds::Dict{Int,Float64}=SPEED_ROADS_URBAN)
```

Find fastest route between `node1` and `node2` and `node3`  on map `m` with assuming `speeds` for road classes.
