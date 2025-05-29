```
LeastSquaresOptimJL(alg = :lm; linsolve = nothing, autodiff::Symbol = :central)
```

Wrapper over [LeastSquaresOptim.jl](https://github.com/matthieugomez/LeastSquaresOptim.jl) for solving `NonlinearLeastSquaresProblem`.

### Arguments

  * `alg`: Algorithm to use. Can be `:lm` or `:dogleg`.

### Keyword Arguments

  * `linsolve`: Linear solver to use. Can be `:qr`, `:cholesky` or `:lsmr`. If `nothing`, then `LeastSquaresOptim.jl` will choose the best linear solver based on the Jacobian structure.
  * `autodiff`: Automatic differentiation / Finite Differences. Can be `:central` or `:forward`.

!!! note
    This algorithm is only available if `LeastSquaresOptim.jl` is installed and loaded.

