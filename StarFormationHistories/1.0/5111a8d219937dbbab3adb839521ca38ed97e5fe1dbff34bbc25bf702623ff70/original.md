```
GaussianDispersion(σ::Real, free::NTuple{1, Bool} = (true,)) <: AbstractDispersionModel
```

Dispersion model for a Gaussian (i.e., Normal) spread in metallicities with standard deviation `σ` (which must be greater than 0) at fixed age. The relative weights for this model are given by $A_{j,k} = \exp(-((x_k - μ_j)/σ)^2/2).$ The `σ` can be fit during optimizations if `free == (true,)` or fixed if `free == (false,)`.

# Examples

```jldoctest; setup=:(using StarFormationHistories: nparams, gradient, update_params, transforms, free_params)
julia> GaussianDispersion(0.2) isa GaussianDispersion{Float64}
true

julia> import Test

julia> Test.@test_throws(ArgumentError, GaussianDispersion(-0.2)) isa Test.Pass
true

julia> nparams(GaussianDispersion(0.2)) == 1
true

julia> GaussianDispersion(0.2)(1.0, 1.2) ≈ exp(-0.5)
true

julia> all(values(gradient(GaussianDispersion(0.2), 1.0, 1.2)) .≈
                (3.0326532985631656, -3.0326532985631656))
true

julia> update_params(GaussianDispersion(0.2), 0.3) == GaussianDispersion(0.3)
true

julia> transforms(GaussianDispersion(0.2)) == (1,)
true

julia> free_params(GaussianDispersion(0.2, (false,))) == (false,)
true
```
