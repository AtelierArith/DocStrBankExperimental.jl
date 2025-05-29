```
surfacetransferloads(self::FEMMHeatDiffSurf,  assembler::A,  geom::NodalField{GFT}, temp::NodalField{FT},  ambtemp::NodalField{FT}) where {A<:AbstractSysvecAssembler, GFT, FT}
```

Compute the load vector corresponding to surface heat transfer.

# Arguments

  * `self` = model machine,
  * `assembler` = matrix assembler
  * `geom` = geometry field,
  * `temp` = temperature field
  * `ambtemp` = ambient temperature field on the surface
