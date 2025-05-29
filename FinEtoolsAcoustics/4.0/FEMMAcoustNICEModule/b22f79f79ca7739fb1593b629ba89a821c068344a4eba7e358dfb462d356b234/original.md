```
acousticstiffness(self::FEMMAcoustNICE, assembler::A, geom::NodalField, P::NodalField{T}) where {T<:Number, A<:AbstractSysmatAssembler}
```

Compute the acoustic mass matrix.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler
  * `geom` = geometry field
  * `P` = acoustic (perturbation) pressure field

Return a matrix.
