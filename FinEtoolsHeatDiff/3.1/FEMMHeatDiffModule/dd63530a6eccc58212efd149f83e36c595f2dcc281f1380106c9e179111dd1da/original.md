```
capacity(self::FEMMHeatDiff,  assembler::A, geom::NodalField{GFT},  temp::NodalField{FT}) where {A<:AbstractSysmatAssembler, GFT, FT}
```

Compute the capacity matrix.

# Arguments

  * `self` = model machine,
  * `assembler` = matrix assembler
  * `geom` = geometry field,
  * `temp` = temperature field
