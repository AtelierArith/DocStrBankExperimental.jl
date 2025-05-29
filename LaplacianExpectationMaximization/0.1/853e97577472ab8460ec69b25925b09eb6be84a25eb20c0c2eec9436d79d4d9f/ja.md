```
OptimizationOptimizer(optimizer, adtype, options)
```

[Optimization.jl](https://docs.sciml.ai/Optimization/stable)を使用します。`options`は`Optimization.solve`に渡されます。

### 例

```using LaplacianExpectationMaximization, Optimization, OptimizationOptimJL, ADTypes OptimizationOptimizer(LBFGS(), AutoForwardDiff(), (;))

```
