```julia
unroll_vertex(
    ng::NestedGraphs.NestedGraph,
    v::Integer
) -> Vector{T} where T<:Integer

```

ネストされたグラフのすべてのネストされたサブグラフに沿ってネストされた頂点を展開します。
