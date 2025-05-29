```julia
mutable struct SubSolvers{Q<:MathOptInterface.AbstractOptimizer, S<:MathOptInterface.AbstractOptimizer, T<:EAGO.ExtensionType}
```

A structure containing the relaxed and upper optimizers to be used, as well as any user-defined extension.

  * `relaxed_optimizer::MathOptInterface.AbstractOptimizer`: Optimizer used to solve relaxed subproblems. Set using `r = [...]` (<: `MOI.AbstractOptimizer`)         (default = `Cbc.Optimizer()`)
  * `upper_optimizer::MathOptInterface.AbstractOptimizer`: Optimizer used to solve upper bounding problems. Set using `u = [...]` (<: `MOI.AbstractOptimizer`)         (default = `Ipopt.Optimizer()`)
  * `ext::EAGO.ExtensionType`: User-defined extension to use. Set using `t = [...]`(<: `EAGO.ExtensionType`)
