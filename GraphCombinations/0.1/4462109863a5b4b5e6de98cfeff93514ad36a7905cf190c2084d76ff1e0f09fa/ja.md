```julia
build_graph(
    graph_rep::Vector{Pair{Int64, Int64}},
    num_vertices::Int64
) -> GraphCombinations.MultigraphWrap{Int64}

```

エッジリストから[`MultigraphWrap`](@ref)を構築します。
