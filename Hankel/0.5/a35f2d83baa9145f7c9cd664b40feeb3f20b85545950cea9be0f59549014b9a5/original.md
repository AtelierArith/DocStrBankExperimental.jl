```
QDHT{p, n}(R, N; dim=1)
QDHT([p, ] R, N; dim=1)
QDHT(p, [n, ] R, N; dim=1)
```

`p`-th order quasi-discrete Hankel transform over aperture radius `R` with `N` samples which transforms along dimension `dim`. If not given, `p` defaults to 0, and `n` the spherical dimension defaults to 1 (cylindrical).

After:

[1] L. Yu, M. Huang, M. Chen, W. Chen, W. Huang, and Z. Zhu, Optics Letters 23 (1998)

[2] M. Guizar-Sicairos and J. C. Gutiérrez-Vega, JOSA A 21, 53 (2004)

[3] H. F. Johnson, Comput. Phys. Commun., 43, 2 (1987)

but with some alterations:

The transform matrix T is not the same as C/T defined in [1, 2] but is more like the form used in equation 14 of [3]. Instead of dividing by $J_1(α_{pn}) J_1(α_{pm})$ we divide by $J_1(α_{pn})^2$. This cancels out the factor between $f$ and $F$ so we do not have to mutltiply (divide) by $J_1(α_{pn})$ ($J_1(α_{pm})$) before and after applying the transform matrix.

Follows [`AbstractFFT`](https://github.com/JuliaMath/AbstractFFTs.jl) approach of applying fwd and inv transform with `mul` and `ldiv`.

To calculate radial integrals of functions sampled using `QDHT`, use [`integrateR`](@ref) and [`integrateK`](@ref).

The type of the coefficients is inferred from the type of `R` (but is promoted to be at least `Float`), so for arbitrary precision use `QDHT([p, ] BigFloat(R), ...)`.
