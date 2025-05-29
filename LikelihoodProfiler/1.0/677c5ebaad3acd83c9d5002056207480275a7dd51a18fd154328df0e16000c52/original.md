```
OptimizationProfiler{S, opType, optsType}
```

A profiler method that uses stepwise re-optimization to profile the likelihood function.

### Fields

  * `stepper::S`: The algorithm used to compute the next profile point.
  * `optimizer::opType`: The optimizer used for the optimization process.
  * `optimizer_opts::optsType`: Options for the optimizer. Defaults to `NamedTuple()`.

### Example

```julia
using Optimization
profiler = OptimizationProfiler(; optimizer = Optimization.LBFGS(), optimizer_opts = (reltol=1e-4,), stepper = FixedStep())
```
