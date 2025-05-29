```
negativity(ρ::QuantumObject, subsys::Int; logarithmic::Bool=false)
```

Compute the [negativity](https://en.wikipedia.org/wiki/Negativity_(quantum_mechanics)) $N(\hat{\rho}) = \frac{\Vert \hat{\rho}^{\Gamma}\Vert_1 - 1}{2}$   where $\hat{\rho}^{\Gamma}$ is the partial transpose of $\hat{\rho}$ with respect to the subsystem,   and $\Vert \hat{X} \Vert_1=\textrm{Tr}\sqrt{\hat{X}^\dagger \hat{X}}$ is the trace norm.

# Arguments

  * `ρ::QuantumObject`: The density matrix (`ρ.type` must be [`Operator`](@ref)).
  * `subsys::Int`: an index that indicates which subsystem to compute the negativity for.
  * `logarithmic::Bool`: choose whether to calculate logarithmic negativity or not. Default as `false`

# Returns

  * `N::Real`: The value of negativity.

# Examples

```jldoctest
julia> Ψ = bell_state(0, 0)

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> ρ = ket2dm(Ψ)

Quantum Object:   type=Operator()   dims=[2, 2]   size=(4, 4)   ishermitian=true
4×4 Matrix{ComplexF64}:
 0.5+0.0im  0.0+0.0im  0.0+0.0im  0.5+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.5+0.0im  0.0+0.0im  0.0+0.0im  0.5+0.0im

julia> round(negativity(ρ, 2), digits=2)
0.5
```
