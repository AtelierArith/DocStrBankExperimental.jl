```
spectralinterpolation(r, s, w=barycentricweights(r))
```

Create the interpolation matrix, type analogous to `r`, for polynomials defined on the points `r` with associated barycentric weights `w` evaluated at the points `s`. See also `barycentricweights` and `spectralderivative`.

# Examples

Create the interpolation matrix which evaluates polynomials on Legendre–Gauss–Lobatto points at an equally spaced grid.

```jldoctest
julia> x, _ = legendregausslobatto(4);
julia> y = collect(-1:0.4:1);
julia> spectralinterpolation(x,y)
6×4 Matrix{Float64}:
  1.0           0.0           0.0           0.0
  0.16          0.936656     -0.136656      0.04
 -0.12          0.868328      0.331672     -0.08
 -0.08          0.331672      0.868328     -0.12
  0.04         -0.136656      0.936656      0.16
 -1.11022e-16   3.43078e-16  -8.98189e-16   1.0
```

# References

Jean-Paul Berrut & Lloyd N. Trefethen, "Barycentric Lagrange Interpolation",   SIAM Review 46 (2004), pp. 501-517.   [https://doi.org/10.1137/S0036144502417715](https://doi.org/10.1137/S0036144502417715)
