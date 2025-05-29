```julia
vertex(
    ng::NestedGraphs.NestedGraph,
    cv::Tuple{T, T} where T<:Integer
) -> Union{Nothing, Int64}

```

Convert a local view `NestedVertex` to a global view
