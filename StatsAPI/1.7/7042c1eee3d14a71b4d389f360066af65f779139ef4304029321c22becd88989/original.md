```
loglikelihood(model::StatisticalModel)
loglikelihood(model::StatisticalModel, observation)
```

Return the log-likelihood of the model.

With an `observation` argument, return the contribution of `observation` to the log-likelihood of `model`.

If `observation` is a `Colon`, return a vector of each observation's contribution to the log-likelihood of the model. In other words, this is the vector of the pointwise log-likelihood contributions.

In general, `sum(loglikehood(model, :)) == loglikelihood(model)`.
