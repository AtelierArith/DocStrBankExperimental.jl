```
IpoptOptimizer(LBFGS::Bool)
```

Setup the [Ipopt](https://coin-or.github.io/Ipopt/) Interior-point Newton method optmizer for parameter estimation.

Ipopt can be configured to use either the Hessian method from the `PEtabODEProblem` (`LBFGS=false`) or an LBFGS scheme (`LBFGS=true`). For setting other Ipopt options, see [`IpoptOptions`](@ref).

See also [`calibrate`](@ref) and [`calibrate_multistart`](@ref).

## Description

Ipopt is an Interior-point Newton method for constrained non-linear optimization problems. More information on the algorithm can be found in [1].

1. Wächter and Biegler, Mathematical programming, pp 25-57 (2006)
