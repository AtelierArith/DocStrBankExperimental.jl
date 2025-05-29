```
ChebyshevSurface{T,N,P,Q} <: ParametricSurface{T,N}
```

Rectangular surface incorporating Chebyshev polynomials as well as radius and conic terms. `T` is the datatype, `N` is the dimensionality, `P` is the number of Chebyshev terms in u and `Q` is the number of Chebyshev terms in v.

The surface is centered at the origin and treated as being the cap of an infinite rectangular prism, thus creating a true half-space. **Note that the surface is vertically offset so that the center (i.e., `(u,v) == (0,0)`) lies at 0 on the z-axis.**

```julia
ChebyshevSurface(halfsizeu, halfsizev, chebycoeff; radius = Inf, conic = 0)
```

`chebycoeff` is a vector containing tuples of the form `(i, j, v)` where `v` is the value of the coefficient $c_{ij}$.

The sag is defined by the equation

$$
z(u,v) = \frac{c(u^2 + v^2)^2}{1 + \sqrt{1 - (1+k)c^2(u^2 + v^2)}} + \sum_{i}^{P}\sum_{j}^{Q}c_{ij}T_i(u)T_j(v)
$$

where $c = \frac{1}{\texttt{radius}}$, $k = \texttt{conic}$ and $T_n$ is the nᵗʰ Chebyshev polynomial of the first kind.
