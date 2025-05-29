```
state(::AbstractSite, ::String)
```

return the local state (as a vector or matrix) corresponding to the site and name given

# Examples

```jldoctest
julia> using TensorMixedStates, .Qubits, .Fermions

julia> state(Qubit(), "+")
2-element Vector{Float64}:
 0.7071067811865475
 0.7071067811865475

julia> state(Fermion(), "FullyMixed")
2×2 Matrix{Float64}:
 0.5  0.0
 0.0  0.5
```
