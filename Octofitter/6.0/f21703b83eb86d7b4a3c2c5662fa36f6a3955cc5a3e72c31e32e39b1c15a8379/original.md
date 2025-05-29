```
using Pigeons
octofit_pigeons(model; nrounds, n_chains=16, n_chains_variational=16)
```

Use Pigeons.jl to sample from intractable posterior distributions. `Pigeons` must be loaded by the user.

```julia
using Pigeons
model = Octofitter.LogDensityModel(System, autodiff=:ForwardDiff, verbosity=4)
chain, pt = octofit_pigeons(model)
```
