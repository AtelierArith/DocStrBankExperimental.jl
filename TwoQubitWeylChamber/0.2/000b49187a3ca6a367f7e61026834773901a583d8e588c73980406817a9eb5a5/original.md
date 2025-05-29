Calculate the maximum gate concurrence.

```julia
C = gate_concurrence(U)
C = gate_concurrence(c₁, c₂, c₃)
```

calculates that maximum concurrence $C ∈ [0, 1]$ that the two two-qubit gate `U`, respectively the gate described by the Weyl chamber coordinates `c₁`, `c₂`, `c₃` (see [`weyl_chamber_coordinates`](@ref)) can generate.

# Reference

  * [KrausPRA2001](@cite) Kraus and Cirac, Phys. Rev. A 63, 062309 (2001)
