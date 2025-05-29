```
acousticABC(self::FEMMAcoustSurf, assembler::A,
  geom::NodalField,
  Pdot::NodalField{T}) where {T<:Number, A<:AbstractSysmatAssembler}
```

Compute the acoustic ABC (Absorbing Boundary Condition) matrix.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler; must be able to assemble unsymmetric matrix
  * `geom` = geometry field
  * `Pdot` = rate of the acoustic (perturbation) pressure field

We assume here that the impedance of this boundary is $ho c$.
