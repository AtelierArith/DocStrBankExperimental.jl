```
bilform_diffusion(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    cf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

Compute the sparse matrix implied by the bilinear form of the "diffusion" type.

$$
\int_{V}  \nabla w \cdot c \cdot \nabla u \; \mathrm{d} V
$$

Here $\nabla w$ is the gradient of the scalar test function, $\nabla u$ is the gradient of the scalar trial function, $c$ is a square symmetric matrix of coefficients or a scalar; $c$ is computed by `cf`, which is a given function (data). Both test and trial functions are assumed to be from the same approximation space. `cf` is represented with [`DataCache`](@ref), and needs to return a symmetric square matrix (to represent general anisotropic diffusion) or a scalar (to represent isotropic diffusion).

The coefficient matrix $c$ can be given in the so-called local material coordinates: coordinates that are attached to a material point and are determined by a local cartesian coordinates system (`mcsys`).

The integral is with respect to the volume of the domain $V$ (i.e. a three dimensional integral).

# Arguments

  * `self` = finite element machine;
  * `assembler` = assembler of the global matrix;
  * `geom` = geometry field;
  * `u` = nodal field to define the degree of freedom numbers;
  * `cf`= data cache, which is called to evaluate the coefficient $c$, given the location of the integration point, the Jacobian matrix, and the finite element label.
