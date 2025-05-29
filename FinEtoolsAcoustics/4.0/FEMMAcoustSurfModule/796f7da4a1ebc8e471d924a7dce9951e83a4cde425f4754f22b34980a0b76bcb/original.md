```
acousticrobin(
    self::FEMMAcoustSurf,
    assembler::A,
    geom::NodalField,
    Pdot::NodalField{T},
    impedance
) where {T<:Number,A<:AbstractSysmatAssembler}
```

Compute the acoustic "Robin boundary condition" (damping) matrix.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler; must be able to assemble unsymmetric matrix
  * `geom` = geometry field
  * `Pdot` = rate of the acoustic (perturbation) pressure field
  * `impedance` = acoustic impedance of the boundary

We assume here that the impedance of this boundary is $ho c$.
