```
AsphericSurface{T,N,Q,M} <: ParametricSurface{T,N}
```

Surface incorporating an aspheric polynomial - radius, conic and aspherics are defined relative to absolute semi-diameter,. `T` is the datatype, `N` is the dimensionality, `Q` is the number of aspheric terms, and `M` is the type of aspheric polynomial. 

```julia
AsphericSurface(semidiameter; radius, conic, aspherics=nothing, normradius = semidiameter)
```

The surface is centered at the origin and treated as being the cap of an infinite cylinder, thus creating a true half-space. Outside of `0 <= ρ <= 1` the height of the surface is not necessarily well defined, so NaN may be returned.

`aspherics`  aspherics should be vectors containing tuples of the form (i, v) where i is the polynomial power of the aspheric term. An empty vector is not permitted. Use `nothing` instead.

The sag is defined by the equation

$$
z(r,\phi) = \frac{cr^2}{1 + \sqrt{1 - (1+k)c^2r^2}} + \sum_{i}^{Q}\alpha_ir^{i}
$$

where $\rho = \frac{r}{\texttt{normradius}}$, $c = \frac{1}{\texttt{radius}}$, and $k = \texttt{conic}$ .

The function checks if the aspheric terms are missing, even, odd or both and uses an efficient polynomial evaluation strategy.
