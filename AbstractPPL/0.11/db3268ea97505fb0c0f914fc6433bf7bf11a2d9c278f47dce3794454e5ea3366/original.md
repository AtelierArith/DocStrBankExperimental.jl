```
predict(
    [rng::AbstractRNG=Random.default_rng(),]
    model::AbstractProbabilisticProgram,
    params,
)
```

Draw a sample from the predictive distribution specified by `model` with its parameters fixed to `params`.
