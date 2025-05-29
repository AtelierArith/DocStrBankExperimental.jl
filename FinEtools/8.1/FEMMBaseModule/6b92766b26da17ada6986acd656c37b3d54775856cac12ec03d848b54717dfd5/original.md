```
bilform_dot(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    cf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

Compute the sparse matrix implied by the bilinear form of the "dot" type.

$$
\int_{\Omega}  \mathbf{w} \cdot \mathbf{c} \cdot \mathbf{u} \; \mathrm{d} \Omega
$$

Here $\mathbf{w}$ is the test function, $\mathbf{u}$ is the trial function, $\mathbf{c}$ is a square matrix of coefficients; $\mathbf {c}$ is computed by `cf`, which is a given function (data). Both trial and test functions are assumed to be vectors(even if of length 1). `cf` is represented with [`DataCache`](@ref), and needs to return a square matrix, with dimension equal to the number of degrees of freedom per node in the `u` field.

The integral domain $\Omega$ can be the volume of the domain $V$ (i.e. a three dimensional integral), or a surface $S$ (i.e. a two dimensional integral), or a line domain $L$ (i.e. a one dimensional integral).

# Arguments

  * `self` = finite element machine;
  * `assembler` = assembler of the global object;
  * `geom` = geometry field;
  * `u` = nodal field to define the degree of freedom numbers;
  * `cf`= data cache, which is called to evaluate the coefficient $c$, given the location of the integration point, the Jacobian matrix, and the finite element label.
  * `m` = manifold dimension (default is 3).
