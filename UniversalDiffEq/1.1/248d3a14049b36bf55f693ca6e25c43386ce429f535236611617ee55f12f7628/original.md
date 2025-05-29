```
predict(UDE::BayesianUDE,test_data::DataFrame;summarize = true,ci = 95,df = true)
```

Uses the Bayesian UDE `UDE` to predict the state of the data `test_data` for each of the sampled parameters in training.

If `summarize` is `true`, this function returns the median prediction as well as the `ci`% lower and upper confidence intervals. Othwerise, it returns all the individual predictions for each sampled parameter.

If `df` is true, this function returns a `DataFrame` object. Otherwise, it returns an `Array` with the predictions.
