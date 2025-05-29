```
spectralderivative(r, w=barycentricweights(r))
```

Create the differentiation matrix, type analogous to `r`, for polynomials defined on the points `r` with associated barycentric weights `w`. See also `barycentricweights` and `spectralinterpolation`.

# Examples

Create the differentiation matrix for Legendre–Gauss–Lobatto points

```jldoctest
julia> x, _ = legendregausslobatto(4);
julia> spectralderivative(x)
4×4 Matrix{Float64}:
 -3.0        4.04508      -1.54508       0.5
 -0.809017   7.77156e-16   1.11803      -0.309017
  0.309017  -1.11803      -1.55431e-15   0.809017
 -0.5        1.54508      -4.04508       3.0
```

# References

Jean-Paul Berrut & Lloyd N. Trefethen, "Barycentric Lagrange Interpolation",   SIAM Review 46 (2004), pp. 501-517.   [https://doi.org/10.1137/S0036144502417715](https://doi.org/10.1137/S0036144502417715)
