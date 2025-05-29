```julia
shock_detector(Se, deg)
shock_detector(Se, deg, S0)
shock_detector(Se, deg, S0, κ)

```

Detect if the solution belongs to a strong discontinuity

*P. O. Persson and J. Peraire. Sub-cell shock capturing for discontinuous Galerkin methods. 44th AIAA Aerospace Sciences Meeting and Exhibit, 2006.*

  * @arg Se = log10(<(u - û)²>/<u²>), u is the solution based on orthogonal polynomials, and û is the same solution with one lower truncated order
  * @arg deg: polynomial degree of freedom
  * @arg S0: reference point of Se
  * @arg κ: empirical parameter that needs to be chosen sufficiently large so as to obtain a sharp but smooth shock profile
