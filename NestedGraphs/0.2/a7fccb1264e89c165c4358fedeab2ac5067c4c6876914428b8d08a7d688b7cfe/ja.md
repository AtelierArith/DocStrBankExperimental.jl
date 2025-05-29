```julia
NestedGraph(
    grv::Array{R<:Graphs.AbstractGraph, 1},
    edges::AbstractVector;
    both_ways
) -> NestedGraphs.NestedGraph{Int64, R} where R<:Graphs.AbstractGraph{Int64}

```

`both_ways`は、エッジが逆方向にも追加されるべきかどうかを制御します。
