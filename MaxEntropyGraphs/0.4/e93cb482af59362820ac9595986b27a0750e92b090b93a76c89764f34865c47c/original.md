```
∇L_BiCM_reduced!(∇L::AbstractVector, θ::AbstractVector, k⊥::Vector, k⊤::Vector, f⊥::Vector, f⊤::Vector,  nz⊥::UnitRange{T}, nz⊤::UnitRange{T}, x::AbstractVector, y::AbstractVector, n⊥::Int) where {T<:Signed}
```

Compute the gradient of the log-likelihood of the reduced DBCM model using the exponential formulation in order to maintain convexity.

For the optimisation, this function will be used togenerate an anonymous function associated with a specific model. The function  will update pre-allocated vectors (`∇L`,`x` and `y`) for speed. The gradient is non-allocating.

# Arguments

  * `∇L`: the gradient of the log-likelihood of the reduced model
  * `θ`: the maximum likelihood parameters of the model ([α; β])
  * `k⊥`: the reduced degree sequence of the ⊥ layer
  * `k⊤`: the reduced degree sequence of the ⊤ layer
  * `f⊥`: the frequency of each degree in the ⊥ layer
  * `f⊤`: the frequency of each degree in the ⊤ layer
  * `nz⊥`: the indices of non-zero elements in the reduced ⊥ layer degree sequence
  * `nz⊤`: the indices of non-zero elements in the reduced ⊤ layer degree sequence
  * `x`: the exponentiated maximum likelihood parameters of the model ( xᵢ = exp(-αᵢ) )
  * `y`: the exponentiated maximum likelihood parameters of the model ( yᵢ = exp(-βᵢ) )
  * `n⊥`: the number unique values in the reduced ⊥ layer degree sequence

# Examples

```jldoctest ∇L_BiCM_reduced
# Explicit use with BiCM model:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> ∇L = zeros(Real, length(model.θᵣ));

julia> x  = zeros(Real, length(model.xᵣ));

julia> y  = zeros(Real, length(model.yᵣ));

julia> ∇model_fun! = θ -> ∇L_BiCM_reduced!(∇L, θ, model.d⊥ᵣ, model.d⊤ᵣ, model.f⊥, model.f⊤, model.d⊥ᵣ_nz, model.d⊤ᵣ_nz, x, y, model.status[:d⊥_unique]);

julia> ∇model_fun!(model.θᵣ);

```
