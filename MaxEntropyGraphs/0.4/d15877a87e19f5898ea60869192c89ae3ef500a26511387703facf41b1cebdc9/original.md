```
degree(m::BiCM, i::Int; method=:reduced)
```

Return the expected degree for node `i` of the BiCM model `m`. Uses the reduced model parameters `xᵣ` for perfomance reasons.

# Arguments

  * `m::BiCM`: the BiCM model
  * `i::Int`: the node for which to compute the degree. This can be any of the nodes in the original graph used to define the model.
  * `method::Symbol`: the method to use for computing the degree. Can be any of the following:

      * `:reduced` (default) uses the reduced model parameters `xᵣ`, `yᵣ`, `f⊥` and `f⊤` for perfomance reasons.
      * `:full` uses all elements of the expected adjacency matrix.
      * `:adjacency` uses the precomputed adjacency matrix `m.Ĝ` of the model.

# Examples

```jldoctest
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([degree(model, 1), degree(model, 1, method=:full), degree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
