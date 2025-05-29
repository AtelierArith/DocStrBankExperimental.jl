```
sprepost(A::AbstractQuantumObject, B::AbstractQuantumObject)
```

Returns the [`SuperOperator`](@ref) form of `A` and `B` acting on the left and right of the density matrix operator, respectively: $\mathcal{O} \left( \hat{A}, \hat{B} \right) \left[ \hat{\rho} \right] = \hat{A} \hat{\rho} \hat{B}$.

Since the density matrix is vectorized in [`OperatorKet`](@ref) form: $|\hat{\rho}\rangle\rangle$, this [`SuperOperator`](@ref) is always a matrix $\hat{B}^T \otimes \hat{A}$, namely

$$
\mathcal{O} \left(\hat{A}, \hat{B}\right) \left[ \hat{\rho} \right] = \hat{B}^T \otimes \hat{A} ~ |\hat{\rho}\rangle\rangle = \textrm{spre}(\hat{A}) * \textrm{spost}(\hat{B}) ~ |\hat{\rho}\rangle\rangle
$$

(see the section in documentation: [Superoperators and Vectorized Operators](@ref doc:Superoperators-and-Vectorized-Operators) for more details)

See also [`spre`](@ref) and [`spost`](@ref).
