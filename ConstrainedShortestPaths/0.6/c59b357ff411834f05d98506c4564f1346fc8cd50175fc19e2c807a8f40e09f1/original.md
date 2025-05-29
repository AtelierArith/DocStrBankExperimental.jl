```julia
basic_shortest_path(
    graph::Graphs.AbstractGraph{T},
    s,
    t;
    ...
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}
basic_shortest_path(
    graph::Graphs.AbstractGraph{T},
    s,
    t,
    distmx::AbstractMatrix;
    bounding
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}

```

Compute shortest path between vertices `s` and `t` of graph `graph`.

# Arguments

  * `graph::AbstractGraph`: acyclic directed graph.
  * `distmx::AbstractMatrix`: `distmx[i, j]` corresponds to the distance between vertices `i` and `j`   along edge `(i, j)` of `graph`.

# Returns

  * `p_star::Vector{Int}`: optimal path found.
  * `c_star::Float64`: length of path `p_star`.
