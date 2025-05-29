```
MAPGPOptimizer(; every = 10, kwargs...)
```

Set the GP hyperparameters to the maximum a posteriori (MAP) estimate `every` number of steps. Run `BayesianOptimization.defaultoptions(MAPGPOptimizer)` to see the default options. By default, all priors are flat. Uniform priors in an interval can be specified by setting the bounds of the form `[lowerbound, upperbound]`, e.g. for a kernel with 3 parameters one would set `kernbounds = [[-3, -3, -4], [2, 3, 1]]`. Non-flat priors can be specified directly on the GP parameters, e.g. `using Distributions; set_priors!(mean, [Normal(0., 1.)])`
