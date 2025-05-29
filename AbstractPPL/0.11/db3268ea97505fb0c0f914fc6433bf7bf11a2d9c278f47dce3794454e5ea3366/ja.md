```
predict(
    [rng::AbstractRNG=Random.default_rng(),]
    model::AbstractProbabilisticProgram,
    params,
)
```

`model`で指定された予測分布から、パラメータを`params`に固定してサンプルを引きます。
