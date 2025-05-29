```
spost(B::AbstractQuantumObject, Id_cache=I(size(B,1)))
```

Returns the [`SuperOperator`](@ref) form of `B` acting on the right of the density matrix operator: $\mathcal{O} \left(\hat{B}\right) \left[ \hat{\rho} \right] = \hat{\rho} \hat{B}$.

Since the density matrix is vectorized in [`OperatorKet`](@ref) form: $|\hat{\rho}\rangle\rangle$, this [`SuperOperator`](@ref) is always a matrix $\hat{B}^T \otimes \hat{\mathbb{1}}$, namely

$$
\mathcal{O} \left(\hat{B}\right) \left[ \hat{\rho} \right] = \hat{B}^T \otimes \hat{\mathbb{1}} ~ |\hat{\rho}\rangle\rangle
$$

(see the section in documentation: [Superoperators and Vectorized Operators](@ref doc:Superoperators-and-Vectorized-Operators) for more details)

The optional argument `Id_cache` can be used to pass a precomputed identity matrix. This can be useful when the same function is applied multiple times with a known Hilbert space dimension.

See also [`spre`](@ref) and [`sprepost`](@ref).
