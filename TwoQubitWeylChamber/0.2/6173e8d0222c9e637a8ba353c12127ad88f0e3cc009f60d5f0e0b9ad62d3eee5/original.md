Calculate the Weyl chamber coordinates c₁, c₂, c₃ for a two-qubit gate.

```julia
c₁, c₂, c₃ = weyl_chamber_coordinates(U)
```

calculates the Weyl chamber coordinates using the algorithm described in [ChildsPRA2003](@citet).

# Reference

  * [ChildsPRA2003](@cite) Childs *et al.*. Phys. Rev. A 68, 052311 (2003)
