```julia
getfoldedgraph(
    ng::NestedGraphs.NestedGraph,
    subgrpaths::Array{Array{T<:Integer, 1}, 1}
) -> Tuple{Graphs.AbstractGraph{T} where T<:Integer, Any}

```

`subgrpaths`で特定されたグラフをノードに置き換えることによってフラットなグラフを取得します。また、マッピングも返します。
