```
L_UBCM_reduced(θ::Vector, K::Vector, F::Vector)
```

Compute the log-likelihood of the reduced UBCM model using the exponential formulation in order to maintain convexity.

# Arguments

  * `θ`: the maximum likelihood parameters of the model
  * `K`: the reduced degree sequence
  * `F`: the frequency of each degree in the degree sequence

The function returns the log-likelihood of the reduced model. For the optimisation, this function will be used to generate an anonymous function associated with a specific model.

# Examples

```jldoctest
# Generic use:
julia> θ = [1.0, 2.0, 3.0, 4.0, 5.0];

julia> K = [1, 2, 3, 4, 5];

julia> F = [1, 2, 3, 4, 5];

julia> L_UBCM_reduced(θ, K, F)
-225.3065566905141
```
