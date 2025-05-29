```
bilform_convection(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    Q::NodalField{QT},
    rhof::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, QT, DC<:DataCache}
```

Compute the sparse matrix implied by the bilinear form of the "convection" type.

$$
\int_{V}  {w} \rho \mathbf{u} \cdot \nabla q \; \mathrm{d} V
$$

Here $w$ is the scalar test function, $\mathbf{u}$ is the convective velocity, $q$ is the scalar trial function, $\rho$ is the mass density; $\rho$ is computed by `rhof`, which is a given function(data). Both test and trial functions are assumed to be from the same approximation space. `rhof` is represented with [`DataCache`](@ref), and needs to return a  scalar mass density.

The integral is with respect to the volume of the domain $V$ (i.e. a three dimensional integral).

# Arguments

  * `self` = finite element machine;
  * `assembler` = assembler of the global matrix;
  * `geom` = geometry field;
  * `u` = convective velocity field;
  * `Q` = nodal field to define the degree of freedom numbers;
  * `rhof`= data cache, which is called to evaluate the coefficient $\rho$, given the location of the integration point, the Jacobian matrix, and the finite element label.
