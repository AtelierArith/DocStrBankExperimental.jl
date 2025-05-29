```
degree(m::UBCM[, v]; method=:reduced)
```

Return a vector corresponding to the expected degree of the UBCM model `m` each node. If v is specified, only return degrees for nodes in v.

# Arguments

  * `m::UBCM`: the UBCM model
  * `v::Vector{Int}`: the nodes for which to compute the degree. Default is all nodes.
  * `method::Symbol`: the method to use for computing the degree. Can be any of the following:

      * `:reduced` (default) uses the reduced model parameters `xᵣ` for perfomance reasons.
      * `:full` uses all elements of the expected adjacency matrix.
      * `:adjacency` uses the precomputed adjacency matrix `m.Ĝ` of the model.

# Examples

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof(degree(model, method=:adjacency)) 
Vector{Float64} (alias for Array{Float64, 1})

```
