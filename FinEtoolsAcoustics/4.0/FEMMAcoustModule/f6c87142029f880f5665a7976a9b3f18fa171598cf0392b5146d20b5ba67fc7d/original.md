```
acousticstiffness(self::FEMMAcoust, assembler::A, geom::NodalField, P::NodalField{T}) where {T<:Number, A<:AbstractSysmatAssembler}
```

Compute the acoustic "stiffness" matrix.

# Arguments

  * `self`   =  acoustics model
  * `assembler`  =  matrix assembler
  * `geom` = geometry field
  * `P` = acoustic (perturbation) pressure field

Return a matrix.

The acoustic "stiffness" matrix is by convention called stiffness, however its mechanical meaning is quite different. (It has to do with kinetic energy.) It is the matrix $\mathbf{K}_a$ in this matrix ODE system for the acoustic pressure:

$$
\mathbf{M}_a \mathbf{\ddot{p}}
+ \mathbf{K}_a \mathbf{{p}} =
\mathbf{{f}}
$$

!!! note
    The bilinear-form function  `bilform_diffusion` from `FinEtools.FEMMBaseModule` is used to compute the matrix.

