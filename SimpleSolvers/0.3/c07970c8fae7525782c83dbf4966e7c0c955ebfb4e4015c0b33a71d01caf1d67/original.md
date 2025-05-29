An `OptimizationAlgorithm` is a datastructe that is used to dispatch on different algorithms.

It needs to implement three important methods,

```
initialize!(alg::OptimizationAlgorithm, ::AbstractVector)
update!(alg::OptimizationAlgorithm, ::AbstractVector)
solver_step!(::AbstractVector, alg::OptimizationAlgorithm)
```

that initialize and update the state of the algorithm and perform an actual optimization step.

Further the following convenience methods should be implemented,

```
objective(alg::OptimizationAlgorithm)
gradient(alg::OptimizationAlgorithm)
hessian(alg::OptimizationAlgorithm)
linesearch(alg::OptimizationAlgorithm)
```

which return the objective to optimize, its gradient and (approximate) Hessian as well as the linesearch algorithm used in conjunction with the optimization algorithm if any.
