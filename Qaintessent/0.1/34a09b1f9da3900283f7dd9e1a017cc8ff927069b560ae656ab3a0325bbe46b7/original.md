```
density_from_statevector(ψ::Vector)
```

Construct density matrix |ψ⟩⟨ψ| (Pauli representation) corresponding to quantum state `ψ`.

```jldoctest
julia> ψ = 1/sqrt(2)[1, -1]; # create ket - state.
julia> ρ = density_from_statevector(ψ)
DensityMatrix([0.9999999999999998, -0.9999999999999998, 0.0, 0.0], 1)
```
