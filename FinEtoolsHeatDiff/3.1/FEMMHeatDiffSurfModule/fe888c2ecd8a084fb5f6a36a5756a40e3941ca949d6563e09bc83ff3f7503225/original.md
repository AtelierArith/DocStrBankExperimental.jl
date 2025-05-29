```
surfacetransfer(self::FEMMHeatDiffSurf,  assembler::A, geom::NodalField{GFT}, temp::NodalField{FT})  where {A<:AbstractSysmatAssembler, GFT, FT}
```

Compute the surface heat transfer matrix.

# Arguments

  * `self` = model machine,
  * `assembler` = matrix assembler
  * `geom` = geometry field,
  * `temp` = temperature field
