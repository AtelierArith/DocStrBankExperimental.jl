```
Fides(hessian_method; verbose::Bool=false)
```

Setup the [Fides](https://github.com/fides-dev/fides) box-constrained Newton-trust region optimizer for parameter estimation.

See also [`calibrate`](@ref) and [`calibrate_multistart`](@ref).

## Arguments

  * `hessian_method`: Method for computing the Hessian. Allowed options are:

      * `nothing`: The Hessian computed by the `PEtabODEProblem` is used.
      * `:BB`: Broyden's "bad" method.
      * `:BFGS`: Broyden-Fletcher-Goldfarb-Shanno update strategy.
      * `:BG`: Broyden's "good" method.
      * `:Broyden`: Broyden-class update scheme.
      * `:SR1`: Symmetric Rank 1 update.
      * `:SSM`: Structured Secant Method.
      * `:TSSM`: Totally Structured Secant Method.
  * `verbose`: Whether to print progress during the parameter estimation.

## Description

Fides is a Newton-trust region optimizer for box-constrained optmization problems. More information on the algorithm can be found in [1]. Fides particularly excels when the full Hessian is too computationally expensive to compute, but a Gauss-Newton Hessian approximation can be computed (for more details see the documentation). In addition to supporting user Hessians via the `PEtabODEProblem`, it supports several Hessian approximation methods. Aa more extensive description than above see the Fides [documentation](https://github.com/fides-dev/fides).

1. Fröhlich and Sorger, PLoS computational biology, pp e1010322 (2022)
