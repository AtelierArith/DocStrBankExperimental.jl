```
DBCM_reduced_iter!(θ::AbstractVector, k_out::AbstractVector, k_in::AbstractVector, F::AbstractVector, nz_out::Vector, nz_in::Vector,x::AbstractVector, y::AbstractVector, G::AbstractVector, H::AbstractVector, n::Int)
```

Compute the next fixed-point iteration for the DBCM model using the exponential formulation in order to maintain convexity. The function is non-allocating and will update pre-allocated vectors (`θ`, `x`, `y` and `G`) for speed.

# Arguments

  * `θ`: the maximum likelihood parameters of the model ([α; β])
  * `k_out`: the reduced outdegree sequence
  * `k_in`: the reduced indegree sequence
  * `F`: the frequency of each pair in the degree sequence
  * `nz_out`: the indices of non-zero elements in the reduced outdegree sequence
  * `nz_in`: the indices of non-zero elements in the reduced indegree sequence
  * `x`: the exponentiated maximum likelihood parameters of the model ( xᵢ = exp(-αᵢ) )
  * `y`: the exponentiated maximum likelihood parameters of the model ( yᵢ = exp(-βᵢ) )
  * `G`: buffer for computations
  * `n`: the number of nodes in the reduced model

# Examples

```jldoctest
# Use with DBCM model:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> G = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> H = zeros(eltype(model.θᵣ), length(model.yᵣ));

julia> x = zeros(eltype(model.θᵣ), length(model.xᵣ));

julia> y = zeros(eltype(model.θᵣ), length(model.yᵣ));

julia> DBCM_FP! = θ -> DBCM_reduced_iter!(θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, x, y, G, model.status[:d_unique]);

julia> DBCM_FP!(model.θᵣ);

```
