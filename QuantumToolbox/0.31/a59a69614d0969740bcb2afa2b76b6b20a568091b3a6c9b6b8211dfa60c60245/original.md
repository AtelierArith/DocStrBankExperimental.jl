```
entropy_vn(ρ::QuantumObject; base::Int=0, tol::Real=1e-15)
```

Calculates the [Von Neumann entropy](https://en.wikipedia.org/wiki/Von_Neumann_entropy) $S = - \textrm{Tr} \left[ \hat{\rho} \log \left( \hat{\rho} \right) \right]$, where $\hat{\rho}$ is the density matrix of the system.

# Notes

  * `ρ` is the quantum state, can be either a [`Ket`](@ref) or an [`Operator`](@ref).
  * `base` specifies the base of the logarithm to use, and when using the default value `0`, the natural logarithm is used.
  * `tol` describes the absolute tolerance for detecting the zero-valued eigenvalues of the density matrix $\hat{\rho}$.

# Examples

Pure state:

```jldoctest
julia> ψ = fock(2,0)

Quantum Object:   type=Ket()   dims=[2]   size=(2,)
2-element Vector{ComplexF64}:
 1.0 + 0.0im
 0.0 + 0.0im

julia> entropy_vn(ψ, base=2)
-0.0
```

Mixed state:

```jldoctest
julia> ρ = maximally_mixed_dm(2)

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=true
2×2 Diagonal{ComplexF64, Vector{ComplexF64}}:
 0.5-0.0im      ⋅    
     ⋅      0.5-0.0im

julia> entropy_vn(ρ, base=2)
1.0
```
