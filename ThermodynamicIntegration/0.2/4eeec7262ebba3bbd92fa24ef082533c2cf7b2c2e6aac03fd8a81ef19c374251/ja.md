```
ThermInt([rng::AbstractRNG]; n_steps=30, n_samples=2000, n_warmup=500)
ThermInt([rng::AbstractRNG], schedule; n_samples=2000, n_warmup=500)
```

  * `schedule` は任意の反復可能なオブジェクトであることができます
  * `n_steps` は、次の式を使用してスケジュールのステップ数です

`(1:n_steps) ./ n_steps).^5`

`ThermInt` オブジェクトは、関数として使用することができます:

```julia
    alg = ThermInt(30)
    alg(loglikelihood, logprior, x_init)
```
