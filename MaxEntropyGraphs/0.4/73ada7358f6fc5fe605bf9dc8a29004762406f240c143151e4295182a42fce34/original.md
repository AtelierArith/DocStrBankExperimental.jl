```
outdegree(m::DBCM[, v]; method=:reduced)
```

Return a vector corresponding to the expected outdegree of the DBCM model `m` each node. If v is specified, only return outdegrees for nodes in v.

# Arguments

  * `m::DBCM`: the DBCM model
  * `v::Vector{Int}`: the nodes for which to compute the outdegree. Default is all nodes.
  * `method::Symbol`: the method to use for computing the outdegree. Can be any of the following:

      * `:reduced` (default) uses the reduced model parameters `xᵣ` for perfomance reasons.
      * `:full` uses all elements of the expected adjacency matrix.
      * `:adjacency` uses the precomputed adjacency matrix `m.Ĝ` of the model.

# Examples

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof(outdegree(model, method=:adjacency)) 
Vector{Float64} (alias for Array{Float64, 1})

```
