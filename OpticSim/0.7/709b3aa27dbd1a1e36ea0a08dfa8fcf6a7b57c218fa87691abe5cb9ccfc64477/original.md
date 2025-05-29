```
ZernikeSurface{T,N,P,Q,M} <: ParametricSurface{T,N}
```

Surface incorporating the Zernike polynomials - radius, conic and aspherics are defined relative to absolute semi-diameter, Zernike terms are normalized according to the `normradius` parameter. `T` is the datatype, `N` is the dimensionality, `P` is the number of Zernike terms, `Q` is the number of aspheric terms and `M` is the Aspheric Type.

The surface is centered at the origin and treated as being the cap of an infinite cylinder, thus creating a true half-space. Outside of `0 <= ρ <= 1` the height of the surface is not necessarily well defined, so NaN may be returned.

For convenience the input `zcoeff` can be indexed using either OSA or Noll convention, indicated using the `indexing` argument as either `ZernikeIndexingOSA` or `ZernikeIndexingNoll`.

```julia
ZernikeSurface(semidiameter, radius = Inf, conic = 0, zcoeff = nothing, aspherics = nothing, normradius = semidiameter, indexing = ZernikeIndexingOSA)
```

`zcoeff` and `aspherics` should be vectors containing tuples of the form `(i, v)` where `i` is either the index of the Zernike term for the corresponding `indexing`, or the polynomial power of the aspheric term (may be even or odd) and  `v` is the corresponding coefficient $A_i$ or $\alpha_i$ respectively..  `M` will be determined from the terms entered to optimize the evaluation of the aspheric polynomial.

The sag is defined by the equation

$$
z(r,\phi) = \frac{cr^2}{1 + \sqrt{1 - (1+k)c^2r^2}} + \sum_{i}^{Q}\alpha_ir^{2i} + \sum_{i}^PA_iZ_i(\rho, \phi)
$$

where $\rho = \frac{r}{\texttt{normradius}}$, $c = \frac{1}{\texttt{radius}}$, $k = \texttt{conic}$ and $Z_n$ is the nᵗʰ Zernike polynomial.
