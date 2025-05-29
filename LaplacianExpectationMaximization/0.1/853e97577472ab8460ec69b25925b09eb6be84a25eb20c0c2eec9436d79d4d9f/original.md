```
OptimizationOptimizer(optimizer, adtype, options)
```

Uses [Optimization.jl](https://docs.sciml.ai/Optimization/stable). `options` are passed to `Optimization.solve`

### Example

``` using LaplacianExpectationMaximization, Optimization, OptimizationOptimJL, ADTypes OptimizationOptimizer(LBFGS(), AutoForwardDiff(), (;))
