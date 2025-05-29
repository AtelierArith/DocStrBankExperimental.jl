```
bilform_div_grad(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    viscf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

Compute the sparse matrix implied by the bilinear form of the "div grad" type.

$$
\int_{V}  \mu \nabla \mathbf{w}:  \nabla\mathbf{u}   \; \mathrm{d} V
$$

Here $\mathbf{w}$ is the vector test function, $\mathbf{u}$ is the velocity, $\mu$ is the dynamic viscosity (or kinematic viscosity, depending on the formulation); $\mu$ is computed by `viscf`, which is a given function (data). Both test and trial functions are assumed to be from the same approximation space. `viscf` is represented with [`DataCache`](@ref), and needs to return a  scalar viscosity.

The integral is with respect to the volume of the domain $V$ (i.e. a three dimensional integral).

# Arguments

  * `self` = finite element machine;
  * `assembler` = assembler of the global matrix;
  * `geom` = geometry field;
  * `u` = velocity field;
  * `viscf`= data cache, which is called to evaluate the coefficient $\mu$, given the location of the integration point, the Jacobian matrix, and the finite element label.
