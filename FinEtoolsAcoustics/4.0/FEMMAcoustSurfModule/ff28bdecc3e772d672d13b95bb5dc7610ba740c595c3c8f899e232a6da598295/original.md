```
pressure2resultantforce(self::FEMMAcoustSurf, assembler::A,
  geom::NodalField,
  P::NodalField{T},
   Force::Field) where {T<:Number, A<:AbstractSysmatAssembler}
```

Compute the rectangular coupling matrix that transcribes given pressure on the surface into the resultant force acting on the surface.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler; must be able to assemble unsymmetric matrix
  * `geom` = geometry field
  * `P` = acoustic (perturbation) pressure field
  * `Force` = field for the force resultant
