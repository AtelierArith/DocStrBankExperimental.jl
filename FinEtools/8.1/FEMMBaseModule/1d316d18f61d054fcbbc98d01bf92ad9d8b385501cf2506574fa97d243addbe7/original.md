```
bilform_lin_elastic(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    cf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

Compute the sparse matrix implied by the bilinear form of the "linearized elasticity" type.

$$
\int_{V} (B \mathbf{w})^T C  B \mathbf{u}   \; \mathrm{d} V
$$

Here $\mathbf{w}$ is the vector test function, $\mathbf{u}$ is the displacement (velocity), $C$ is the elasticity (viscosity) matrix; $C$ is computed by `cf`, which is a given function(data). Both test and trial functions are assumed to be from the same approximation space. `cf` is represented with [`DataCache`](@ref), and needs to return a matrix of the appropriate size.

The integral is with respect to the volume of the domain $V$ (i.e. a three dimensional integral).

# Arguments

  * `self` = finite element machine;
  * `assembler` = assembler of the global matrix;
  * `geom` = geometry field;
  * `u` = velocity field;
  * `viscf`= data cache, which is called to evaluate the coefficient $\mu$, given the location of the integration point, the Jacobian matrix, and the finite element label.
