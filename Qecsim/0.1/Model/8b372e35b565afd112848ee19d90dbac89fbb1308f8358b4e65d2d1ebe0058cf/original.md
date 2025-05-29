```
generate(error_model, code, p::Real, [rng::AbstractRNG=GLOBAL_RNG]) -> BitVector
```

Generate a new error in binary symplectic form according to the `error_model` and `code`, where `p` is typically the probability of an error on a single qubit.

!!! note "Abstract method"
    This method should be implemented for concrete subtypes or duck-typed implementations of [`ErrorModel`](@ref).

