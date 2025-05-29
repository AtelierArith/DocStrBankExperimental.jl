```
pressure2resultanttorque(self::FEMMAcoustSurf, assembler::A,
  geom::NodalField,
  P::NodalField{T},
  Torque::GeneralField, CG::FFltVec) where {T<:Number, A<:AbstractSysmatAssembler}
```

Compute the rectangular coupling matrix that transcribes given pressure on the surface into the resultant torque acting on the surface with respect to the CG.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler; must be able to assemble unsymmetric matrix
  * `geom` = geometry field
  * `P` = acoustic (perturbation) pressure field
  * `Torque` = field for the torque resultant
