```julia
roll_vertex(
    ng::NestedGraphs.NestedGraph,
    v::AbstractArray{T<:Integer, 1}
) -> Union{Nothing, Int64}

```

Given a vector of the nested inner subgraphs get the index in the flat graph. The last element of the vector is handled as the node number in the `v[1:end-1]` inner nested graph
