```
linform_dot(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    P::NodalField{T},
    f::DC,
    m,
) where {FEMM<:AbstractFEMM, A<:AbstractSysvecAssembler, FT<:Number, T, DC<:DataCache}
```

Compute the discrete vector implied by the linear form "dot".

$$
\int_{V}  \mathbf{w} \cdot \mathbf{f} \; \mathrm{d} V
$$

Here $\mathbf{w}$ is the test function, $\mathbf{f}$ is a given function (data). Both are assumed to be vectors,  even if they are of length 1, representing scalars. The data $\mathbf{f}$ is represented with [`DataCache`](@ref).

# Arguments

  * `self` = finite element machine;
  * `assembler` = assembler of the global vector;
  * `geom` = geometry field;
  * `P` = nodal field to define the degree of freedom numbers;
  * `f`= data cache, which is called to evaluate the integrand based on the location, the Jacobian matrix, the finite element identifier, and the quadrature point;
  * `m`= manifold dimension, 0= vertex (point), 1= curve, 2= surface, 3= volume. For body loads `m` is set to 3, for tractions on the surface it is set to 2, and so on.
