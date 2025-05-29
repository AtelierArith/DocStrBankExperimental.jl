```julia
resource_shortest_path(
    graph::Graphs.AbstractGraph{T},
    s,
    t,
    max_costs::AbstractVector,
    distmx::AbstractMatrix,
    costmx::Array{Float64, 3};
    bounding
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}

```

Compute resource contrained shortest path between vertices `s` and `t` of graph `g`.

# Arguments

  * `g::AbstractGraph`: acyclic directed graph.
  * `max_costs::AbstractVector`: list of upper bounds for each resource constraint.
  * `distmx::AbstractMatrix`: `distmx[i, j]` corresponds to the distance between vertices `i` and `j`   along edge `(i, j)` of `g`.
  * `costmx::Array{Float64, 3}`: `cost_mx[i, j, k]` corresponds to the resource cost of edge `(i, j)` for the `k`th resource constraint.

# Returns

  * `p_star::Vector{Int}`: optimal path found.
  * `c_star::Float64`: length of path `p_star`.
