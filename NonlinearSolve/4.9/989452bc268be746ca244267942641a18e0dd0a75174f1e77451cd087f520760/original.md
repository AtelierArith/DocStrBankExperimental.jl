```
CMINPACK(; method::Symbol = :auto, autodiff = missing)
```

### Keyword Arguments

  * `method`: the choice of method for the solver.
  * `autodiff`: Defaults to `missing`, which means we will default to letting `MINPACK` construct the jacobian if `f.jac` is not provided. In other cases, we use it to generate a jacobian similar to other NonlinearSolve solvers.

### Submethod Choice

The keyword argument `method` can take on different value depending on which method of `fsolve` you are calling. The standard choices of `method` are:

  * `:hybr`: Modified version of Powell's algorithm. Uses MINPACK routine [`hybrd1`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/hybrd1.c)
  * `:lm`: Levenberg-Marquardt. Uses MINPACK routine [`lmdif1`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/lmdif1.c)
  * `:lmdif`: Advanced Levenberg-Marquardt (more options available with `; kwargs...`). See MINPACK routine [`lmdif`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/lmdif.c) for more information
  * `:hybrd`: Advanced modified version of Powell's algorithm (more options available with `; kwargs...`). See MINPACK routine [`hybrd`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/hybrd.c) for more information

If a Jacobian is supplied as part of the [`NonlinearFunction`](@ref nonlinearfunctions), then the following methods are allowed:

  * `:hybr`: Advanced modified version of Powell's algorithm with user supplied Jacobian. Additional arguments are available via `; kwargs...`. See MINPACK routine [`hybrj`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/hybrj.c) for more information
  * `:lm`: Advanced Levenberg-Marquardt with user supplied Jacobian. Additional arguments are available via `; kwargs...`. See MINPACK routine [`lmder`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/lmder.c) for more information

The default choice of `:auto` selects `:hybr` for NonlinearProblem and `:lm` for NonlinearLeastSquaresProblem.

!!! note
    This algorithm is only available if `MINPACK.jl` is installed and loaded.

