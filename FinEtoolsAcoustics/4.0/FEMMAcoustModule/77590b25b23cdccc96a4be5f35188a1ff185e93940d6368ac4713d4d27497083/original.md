```
acousticmass(self::FEMMAcoust, assembler::A,
  geom::NodalField,
  Pddot::NodalField{T}) where {T<:Number,
  A<:AbstractSysmatAssembler}
```

Compute the acoustic mass matrix.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler
  * `geom` = geometry field
  * `Pddot` = second order rate of the acoustic (perturbation) pressure field

The acoustic "mass" matrix is by convention called mass, however its mechanical meaning is quite different. (It has to do with potential energy.) It is the matrix $\mathbf{M}_a$ in this matrix ODE system for the acoustic pressure:

$$
\mathbf{M}_a \mathbf{\ddot{p}}
+ \mathbf{K}_a \mathbf{{p}} =
\mathbf{{f}}
$$

!!! note
    The bilinear-form function  `bilform_dot`  from `FinEtools.FEMMBaseModule` is used to compute the matrix.

