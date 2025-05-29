```
entropy_relative(ρ::QuantumObject, σ::QuantumObject; base::Int=0, tol::Real=1e-15)
```

Calculates the [quantum relative entropy](https://en.wikipedia.org/wiki/Quantum_relative_entropy) of $\hat{\rho}$ with respect to $\hat{\sigma}$: $D(\hat{\rho}||\hat{\sigma}) = \textrm{Tr} \left[ \hat{\rho} \log \left( \hat{\rho} \right) \right] - \textrm{Tr} \left[ \hat{\rho} \log \left( \hat{\sigma} \right) \right]$.

# Notes

  * `ρ` is a quantum state, can be either a [`Ket`](@ref) or an [`Operator`](@ref).
  * `σ` is a quantum state, can be either a [`Ket`](@ref) or an [`Operator`](@ref).
  * `base` specifies the base of the logarithm to use, and when using the default value `0`, the natural logarithm is used.
  * `tol` describes the absolute tolerance for detecting the zero-valued eigenvalues of the density matrix $\hat{\rho}$.

# References

  * [Nielsen-Chuang2011; section 11.3.1, page 511](@citet)
