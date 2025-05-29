```
optimize!(stochasticprogram::StochasticProgram; crash::AbstractCrash = Crash.None(), cache::Bool = false; kw...)
```

Optimize the `stochasticprogram` in expectation. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown. An optional crash procedure can be set to warm-start. Setting the `cache` flag to true will, upon sucessful termination, try to cache the solution values for all relevant attributes in the model. The values will then persist after future `evaluate` calls that would otherwise overwrite the optimal solution.

## Examples

The following solves the stochastic program `sp` using the L-shaped algorithm.

```julia
set_optimizer(sp, LShaped.Optimizer)
set_optimizer_attribute(sp, MasterOptimizer(), GLPK.Optimizer)
set_optimizer_attribute(sp, SubProblemOptimizer(), GLPK.Optimizer)
optimize!(sp);

# output

L-Shaped Gap  Time: 0:00:02 (6 iterations)
  Objective:       -855.8333333333358
  Gap:             0.0
  Number of cuts:  8
  Iterations:      6
```

The following solves the stochastic program `sp` using GLPK on the extended form.

```julia
using GLPK

set_optimizer(sp, GLPK.Optimizer)
optimize!(sp)

```

See also: [`VRP`](@ref)
