```
SemOptimizerOptim{A, B} <: SemOptimizer{:Optim}
```

Connects to `Optim.jl` as the optimization backend.

# Constructor

```
SemOptimizerOptim(;
    algorithm = LBFGS(),
    options = Optim.Options(;f_reltol = 1e-10, x_abstol = 1.5e-8),
    kwargs...)
```

# Arguments

  * `algorithm`: optimization algorithm from `Optim.jl`
  * `options::Optim.Options`: options for the optimization algorithm

# Usage

All algorithms and options from the Optim.jl library are available, for more information see the Optim.jl online documentation.

# Examples

```julia
my_optimizer = SemOptimizerOptim()

# hessian based optimization with backtracking linesearch and modified initial step size
using Optim, LineSearches

my_newton_optimizer = SemOptimizerOptim(
    algorithm = Newton(
        ;linesearch = BackTracking(order=3),
        alphaguess = InitialHagerZhang()
    )
)
```

# Extended help

## Constrained optimization

When using the `Fminbox` or `SAMIN` constrained optimization algorithms, the vector or dictionary of lower and upper bounds for each model parameter can be specified via `lower_bounds` and `upper_bounds` keyword arguments. Alternatively, the `lower_bound` and `upper_bound` keyword arguments can be used to specify the default bound for all non-variance model parameters, and the `variance_lower_bound` and `variance_upper_bound` keyword – for the variance parameters (the diagonal of the *S* matrix).

## Interfaces

  * `algorithm(::SemOptimizerOptim)`
  * `options(::SemOptimizerOptim)`

## Implementation

Subtype of `SemOptimizer`.
