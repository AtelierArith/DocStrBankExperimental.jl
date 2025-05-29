```
GPLikelihood(obs, data, kernelfn, prior::AbstractSimulatorPrior, name=nameof(obs))
```

Constructs a GP likelihood from the given observable, data, kernel function, and prior. The kernel function should be a function that takes parameters matching those sampled from `prior` and constructs any `Kernel` from `KernelFunctions`.
