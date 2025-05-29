```
returnTuringParams(model, params; maxiters = 1e3,alg=Rodas5(),abstol=1e-8, reltol=1e-6, tspan=1e4,ensemblealg=EnsembleThreads(),batch_size=1e4)
```

Return a `save_turing` object of parameters that are predicted to be pattern forming.

Required inputs:

  * `model`: specified via the `@reaction_network` macro
  * `params`: all reaction and diffusion parameters, in a `model_parameters` object

Optional inputs:

  * `batch_size`: the number of parameter sets to consider at once. Increasing/decreasing from the default value may improve speed.

Inputs carried over from DifferentialEquations.jl; see [here](https://docs.sciml.ai/DiffEqDocs/stable/) for further details:

  * `maxiters`: maximum number of iterations to reach steady state (otherwise simulation terminates)
  * `alg`: ODE solver algorithm
  * `abstol` and `reltol`: tolerance levels of solvers
  * `tspan`: maximum time allowed to reach steady state (otherwise simulation terminates)
  * `ensemblealg`: ensemble simulation method
