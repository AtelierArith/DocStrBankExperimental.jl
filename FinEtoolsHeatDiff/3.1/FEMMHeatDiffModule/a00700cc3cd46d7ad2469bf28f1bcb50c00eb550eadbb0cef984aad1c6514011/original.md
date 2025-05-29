```
conductivity(self::FEMMHeatDiff,  assembler::A, geom::NodalField{GFT},  temp::NodalField{FT}) where {A<:AbstractSysmatAssembler, GFT, FT}
```

Compute the conductivity matrix.

# Arguments

  * `self` = model machine,
  * `assembler` = matrix assembler
  * `geom` = geometry field,
  * `temp` = temperature field
