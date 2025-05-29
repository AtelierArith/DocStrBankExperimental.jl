State defined by a stabilizer tableau

For full functionality you also need to import the `QuantumClifford` library.

```jldoctest
julia> using QuantumClifford, QuantumOptics # needed for the internal representation of the stabilizer tableaux and the conversion to a ket

julia> StabilizerState(S"XX ZZ")
𝒮₂

julia> express(StabilizerState(S"-X"))
Ket(dim=2)
  basis: Spin(1/2)
  0.7071067811865475 + 0.0im
 -0.7071067811865475 + 0.0im
```
