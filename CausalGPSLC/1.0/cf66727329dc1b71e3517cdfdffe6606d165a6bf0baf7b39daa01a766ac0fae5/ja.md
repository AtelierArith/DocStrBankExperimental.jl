```
samplePosterior(hyperparameters, priorparameters, SigmaU, X, T, Y)
```

観測データに基づいて事後分布からサンプルを引きます。パラメータ:

  * `hyperparams::`[`HyperParameters`](@ref)
  * `priorparams::`[`PriorParameters`](@ref)
  * `SigmaU::`[`ConfounderStructure`](@ref)
  * `X::`[`Covariates`](@ref)
  * `T::`[`Treatment`](@ref)
  * `Y::`[`Outcome`](@ref)

事後サンプルはGenの選択マップのベクターとして返されます。
