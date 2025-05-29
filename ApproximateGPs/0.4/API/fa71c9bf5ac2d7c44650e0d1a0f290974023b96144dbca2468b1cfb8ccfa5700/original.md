```
approx_lml(approx::<Approximation>, lfx::LatentFiniteGP, ys)
```

Compute an approximation to the log of the marginal likelihood (also known as "evidence") under the given `approx` to the posterior. This approximation can be used to optimise the hyperparameters of `lfx`.

This should become part of the AbstractGPs API (see JuliaGaussianProcesses/AbstractGPs.jl#221).
