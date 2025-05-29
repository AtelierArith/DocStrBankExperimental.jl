```
GeneralizedDFSane(; linesearch, sigma_min, sigma_max, sigma_1, name::Symbol = :unknown)
```

A generalized version of the DF-SANE algorithm. This algorithm is a Jacobian-Free Spectral Method.

### Arguments

  * `linesearch`: Globalization using a Line Search Method. This is not optional currently, but that restriction might be lifted in the future.
  * `sigma_min`: The minimum spectral parameter allowed. This is used to ensure that the spectral parameter is not too small.
  * `sigma_max`: The maximum spectral parameter allowed. This is used to ensure that the spectral parameter is not too large.
  * `sigma_1`: The initial spectral parameter. If this is not provided, then the algorithm initializes it as `sigma_1 = <u, u> / <u, f(u)>`.
