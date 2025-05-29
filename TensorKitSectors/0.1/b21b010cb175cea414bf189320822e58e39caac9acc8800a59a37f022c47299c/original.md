```
Nsymbol(a::I, b::I, c::I) where {I<:Sector} -> Integer
```

Return an `Integer` representing the number of times `c` appears in the fusion product `a ⊗ b`. Could be a `Bool` if `FusionStyle(I) == UniqueFusion()` or `SimpleFusion()`.
