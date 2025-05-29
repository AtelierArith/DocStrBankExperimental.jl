```
L_BiCM_reduced(θ::Vector, k⊥::Vector, k⊤::Vector, f⊥::Vector, f⊤::Vector, nz⊥::UnitRange, nz⊤::UnitRange, n⊥ᵣ::Int)
```

Compute the log-likelihood of the reduced BiCM model using the exponential formulation in order to maintain convexity.

# Arguments

  * `θ`: the maximum likelihood parameters of the model ([α; β])
  * `k⊥`: the reduced degree sequence of the ⊥ layer
  * `k⊤`: the reduced degree sequence of the ⊤ layer
  * `f⊥`: the frequency of each degree in the ⊥ layer
  * `f⊤`: the frequency of each degree in the ⊤ layer
  * `nz⊥`: the indices of non-zero elements in the reduced ⊥ layer degree sequence
  * `nz⊤`: the indices of non-zero elements in the reduced ⊤ layer degree sequence
  * `n⊥ᵣ`: the number unique values in the reduced ⊥ layer degree sequence

The function returns the log-likelihood of the reduced model. For the optimisation, this function will be used to generate an anonymous function associated with a specific model.

# Examples

```jldoctest
# Generic use:
julia> k⊥ = [1, 2, 3, 4];

julia> k⊤  = [1, 2, 4];

julia> f⊥  = [1; 3; 1; 1];

julia> f⊤  = [4; 2; 1];

julia> nz⊥ = 1:length(k⊥);

julia> nz⊤ = 1:length(k⊤);

julia> n⊥ᵣ = length(k⊥);

julia> θ   = collect(range(0.1, step=0.1, length=length(k⊥) + length(k⊤)));

julia> L_BiCM_reduced(θ, k⊥, k⊤, f⊥, f⊤, nz⊥, nz⊤, n⊥ᵣ)
-26.7741690720244
```

```jldoctest
# Use with DBCM model:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> model_fun = θ -> L_BiCM_reduced(θ, model.d⊥ᵣ, model.d⊤ᵣ, model.f⊥, model.f⊤, model.d⊥ᵣ_nz, model.d⊤ᵣ_nz, model.status[:d⊥_unique]);

julia> model_fun(ones(size(model.θᵣ)))
-237.5980041411147
```
