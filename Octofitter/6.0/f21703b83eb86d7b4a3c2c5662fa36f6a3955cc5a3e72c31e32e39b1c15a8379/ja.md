```
using Pigeons
octofit_pigeons(model; nrounds, n_chains=16, n_chains_variational=16)
```

Pigeons.jlを使用して、扱いきれない事後分布からサンプリングします。`Pigeons`はユーザーによってロードされる必要があります。

```julia
using Pigeons
model = Octofitter.LogDensityModel(System, autodiff=:ForwardDiff, verbosity=4)
chain, pt = octofit_pigeons(model)
```
