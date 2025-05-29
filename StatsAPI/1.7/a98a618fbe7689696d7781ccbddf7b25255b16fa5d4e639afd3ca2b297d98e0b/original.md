```
deviance(model::StatisticalModel)
```

Return the deviance of the model relative to a reference, which is usually when applicable the saturated model. It is equal, *up to a constant*, to $-2 \log L$, with $L$ the likelihood of the model.
