```julia
stochastic_routing_shortest_path_with_threshold(
    graph::Graphs.AbstractGraph{T},
    slacks::AbstractMatrix,
    delays::AbstractMatrix;
    ...
)
stochastic_routing_shortest_path_with_threshold(
    graph::Graphs.AbstractGraph{T},
    slacks::AbstractMatrix,
    delays::AbstractMatrix,
    λ_values::AbstractVector;
    origin_vertex,
    destination_vertex,
    bounding,
    use_convex_resources,
    threshold
)

```

Threshold version of [`stochastic_routing_shortest_path`](@ref).
