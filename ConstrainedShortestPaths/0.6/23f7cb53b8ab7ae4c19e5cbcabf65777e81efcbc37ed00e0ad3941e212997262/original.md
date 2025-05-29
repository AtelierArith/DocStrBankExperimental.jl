```julia
stochastic_routing_shortest_path(
    graph::Graphs.AbstractGraph{T},
    slacks::AbstractMatrix,
    intrinsic_delays::AbstractMatrix;
    ...
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}
stochastic_routing_shortest_path(
    graph::Graphs.AbstractGraph{T},
    slacks::AbstractMatrix,
    intrinsic_delays::AbstractMatrix,
    λ_values::AbstractVector;
    origin_vertex,
    destination_vertex,
    bounding,
    use_convex_resources
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}

```

Compute stochastic routing shortest path between `origin_vertex` and `destination_vertex` vertices of graph `graph`.

# Arguments

  * `graph::AbstractGraph`: acyclic directed graph.
  * `slacks`: `slacks[i, j]` corresponds to the time slack between `i` and `j`.
  * `delays`: `delays[i, ω]` corresponds to delay of `i` for scenario `ω`.

# Returns

  * `p_star::Vector{Int}`: optimal path found.
  * `c_star::Float64`: length of path `p_star`.
