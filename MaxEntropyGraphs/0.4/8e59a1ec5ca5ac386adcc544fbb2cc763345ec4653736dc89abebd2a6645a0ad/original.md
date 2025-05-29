```
outdegree(m::DBCM, i::Int; method=:reduced)
```

Return the expected degree vector for node `i` of the DBCM model `m`. Uses the reduced model parameters `xᵣ` for perfomance reasons.

# Arguments

  * `m::DBCM`: the DBCM model
  * `i::Int`: the node for which to compute the degree.
  * `method::Symbol`: the method to use for computing the degree. Can be any of the following:

      * `:reduced` (default) uses the reduced model parameters `xᵣ` for perfomance reasons.
      * `:full` uses all elements of the expected adjacency matrix.
      * `:adjacency` uses the precomputed adjacency matrix `m.Ĝ` of the model.

# Examples

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([outdegree(model, 1), outdegree(model, 1, method=:full), outdegree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
