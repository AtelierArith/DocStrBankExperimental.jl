```
generate(
    error_model::SimpleErrorModel, code, p::Real, [rng::AbstractRNG=GLOBAL_RNG]
) -> BitVector
```

Generate a new IID error based on [`Model.probability_distribution`](@ref). See also [`Model.generate`](@ref).

!!! note
    The method [`Model.probability_distribution`](@ref) should be implemented for concrete subtypes of [`SimpleErrorModel`](@ref).

