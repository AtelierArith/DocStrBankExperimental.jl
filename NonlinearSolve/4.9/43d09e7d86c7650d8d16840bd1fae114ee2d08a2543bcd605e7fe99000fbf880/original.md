```
FastLevenbergMarquardtJL(
    linsolve::Symbol = :cholesky;
    factor = 1e-6, factoraccept = 13.0, factorreject = 3.0, factorupdate = :marquardt,
    minscale = 1e-12, maxscale = 1e16, minfactor = 1e-28, maxfactor = 1e32,
    autodiff = nothing
)
```

Wrapper over [FastLevenbergMarquardt.jl](https://github.com/kamesy/FastLevenbergMarquardt.jl) for solving `NonlinearLeastSquaresProblem`. For details about the other keyword arguments see the documentation for `FastLevenbergMarquardt.jl`.

### Arguments

  * `linsolve`: Linear solver to use. Can be `:qr` or `:cholesky`.

### Keyword Arguments

  * `autodiff`: determines the backend used for the Jacobian. Note that this argument is ignored if an analytical Jacobian is passed, as that will be used instead. Defaults to `nothing` which means that a default is selected according to the problem specification!

!!! note
    This algorithm is only available if `FastLevenbergMarquardt.jl` is installed and loaded.

