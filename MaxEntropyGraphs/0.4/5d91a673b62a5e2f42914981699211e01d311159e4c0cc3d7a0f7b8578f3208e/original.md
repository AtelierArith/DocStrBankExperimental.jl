```
BiCM_reduced_iter!(θ::AbstractVector, k⊥::Vector, k⊤::Vector, f⊥::Vector, f⊤::Vector, nz⊥::UnitRange{T}, nz⊤::UnitRange{T}, x::AbstractVector, y::AbstractVector, G::AbstractVector, n⊥::Int) where {T<:Signed}
```

Compute the next fixed-point iteration for the BiCM model using the exponential formulation in order to maintain convexity. The function is non-allocating and will update pre-allocated vectors (`θ`, `x`, `y` and `G`) for speed.

# Arguments

  * `θ`: the maximum likelihood parameters of the model ([α; β])
  * `k⊥`: the reduced degree sequence of the ⊥ layer
  * `k⊤`: the reduced degree sequence of the ⊤ layer
  * `f⊥`: the frequency of each degree in the ⊥ layer
  * `f⊤`: the frequency of each degree in the ⊤ layer
  * `nz⊥`: the indices of non-zero elements in the reduced ⊥ layer degree sequence
  * `nz⊤`: the indices of non-zero elements in the reduced ⊤ layer degree sequence
  * `x`: the exponentiated maximum likelihood parameters of the model ( xᵢ = exp(-αᵢ) )
  * `y`: the exponentiated maximum likelihood parameters of the model ( yᵢ = exp(-βᵢ) )
  * `G`: buffer for computations
  * `n⊥`: the number unique values in the reduced ⊥ layer degree sequence

# Examples

```jldoctest
# Use with BiCM model:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> G = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> x = zeros(eltype(model.θᵣ), length(model.xᵣ));

julia> y = zeros(eltype(model.θᵣ), length(model.yᵣ));


julia> BiCM_FP! = θ -> BiCM_reduced_iter!(θ, model.d⊥ᵣ, model.d⊤ᵣ, model.f⊥, model.f⊤, model.d⊥ᵣ_nz, model.d⊤ᵣ_nz, x, y, G, model.status[:d⊥_unique]);

julia> BiCM_FP!(model.θᵣ);

```
