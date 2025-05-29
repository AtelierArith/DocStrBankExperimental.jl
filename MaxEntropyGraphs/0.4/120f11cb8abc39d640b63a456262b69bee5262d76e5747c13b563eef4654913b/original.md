```
degree(m::UBCM, i::Int; method=:reduced)
```

Return the expected degree for node `i` of the UBCM model `m`. Uses the reduced model parameters `xᵣ` for perfomance reasons.

# Arguments

  * `m::UBCM`: the UBCM model
  * `i::Int`: the node for which to compute the degree.
  * `method::Symbol`: the method to use for computing the degree. Can be any of the following:

      * `:reduced` (default) uses the reduced model parameters `xᵣ` for perfomance reasons.
      * `:full` uses all elements of the expected adjacency matrix.
      * `:adjacency` uses the precomputed adjacency matrix `m.Ĝ` of the model.

# Examples

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([degree(model, 1), degree(model, 1, method=:full), degree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
