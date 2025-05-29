```
spre(A::AbstractQuantumObject, Id_cache=I(size(A,1)))
```

Returns the [`SuperOperator`](@ref) form of `A` acting on the left of the density matrix operator: $\mathcal{O} \left(\hat{A}\right) \left[ \hat{\rho} \right] = \hat{A} \hat{\rho}$.

Since the density matrix is vectorized in [`OperatorKet`](@ref) form: $|\hat{\rho}\rangle\rangle$, this [`SuperOperator`](@ref) is always a matrix $\hat{\mathbb{1}} \otimes \hat{A}$, namely 

$$
\mathcal{O} \left(\hat{A}\right) \left[ \hat{\rho} \right] = \hat{\mathbb{1}} \otimes \hat{A} ~ |\hat{\rho}\rangle\rangle
$$

(see the section in documentation: [Superoperators and Vectorized Operators](@ref doc:Superoperators-and-Vectorized-Operators) for more details)

The optional argument `Id_cache` can be used to pass a precomputed identity matrix. This can be useful when the same function is applied multiple times with a known Hilbert space dimension.

See also [`spost`](@ref) and [`sprepost`](@ref).
