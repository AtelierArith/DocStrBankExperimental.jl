```
probability_distribution(error_model, p::Real) -> NTuple{4,Real}
```

Return the single-qubit probability distribution amongst Pauli I, X, Y and Z, where `p` is the overall probability of an error on a single qubit.

!!! note "Abstract method [optional]"
    This method is **not** invoked by any core modules. Since it is often useful for decoders, it is provided as a template and concrete subtypes or duck-typed implementations of [`ErrorModel`](@ref) are encouraged to implement it when appropriate, particularly for IID error models.

