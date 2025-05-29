```
ev_integrate(
        self::FEMM,
        geom::NodalField{FT},
        f::DC,
        initial::R,
        m,
) where {FEMM<:AbstractFEMM, FT<:Number, DC<:DataCache, R}
```

Compute the integral of a given function over a mesh domain.

$$
\int_{\Omega}  {f} \; \mathrm{d} \Omega
$$

Here ${f}$ is a given function (data).  The data ${f}$ is represented with [`DataCache`](@ref).

# Arguments

  * `self` = finite element machine;
  * `geom` = geometry field;
  * `f`= data cache, which is called to evaluate the integrand based on the location, the Jacobian matrix, the finite element identifier, and the quadrature point;
  * `initial` = initial value of the integral,
  * `m`= manifold dimension, 0= vertex (point), 1= curve, 2= surface, 3= volume. For body loads `m` is set to 3, for tractions on the surface it is set to 2, and so on.
