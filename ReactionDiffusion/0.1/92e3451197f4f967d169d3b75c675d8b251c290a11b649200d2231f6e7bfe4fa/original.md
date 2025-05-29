```
simulate(model,param;alg=KenCarp4(),reltol=1e-6,abstol=1e-8, dt = 0.1, maxiters = 1e3, save_everystep = true)
```

Simulate `model` for a single parameter set `param`.

Required inputs:

  * `model`: specified via the `@reaction_network` macro
  * `param`: all reaction and diffusion parameters, in a `model_parameters` object. *This must be a single parameter set only*

Inputs carried over from DifferentialEquations.jl; see [here](https://docs.sciml.ai/DiffEqDocs/stable/) for further details:

  * `maxiters`: maximum number of iterations to reach steady state (otherwise simulation terminates)
  * `alg`: solver algorithm
  * `abstol` and `reltol`: tolerance levels of solvers
  * `dt`: initial value for timestep
  * `save_everystep`: controls whether all timepoints are saved, defaults to `true`
