```
variance(O::QuantumObject, ψ::Union{QuantumObject,Vector{QuantumObject}})
```

Variance of the [`Operator`](@ref) `O`: $\langle\hat{O}^2\rangle - \langle\hat{O}\rangle^2$,

where $\langle\hat{O}\rangle$ is the expectation value of `O` with the state `ψ` (see also [`expect`](@ref)), and the state `ψ` can be a [`Ket`](@ref), [`Bra`](@ref) or [`Operator`](@ref).

The function returns a real number if `O` is hermitian, and returns a complex number otherwise.

Note that `ψ` can also be given as a list of [`QuantumObject`](@ref), it returns a list of expectation values.
