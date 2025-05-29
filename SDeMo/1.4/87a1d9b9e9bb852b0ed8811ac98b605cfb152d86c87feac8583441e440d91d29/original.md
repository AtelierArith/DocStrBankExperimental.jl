```
StatsAPI.predict(ensemble::Ensemble, X; consensus = median, kwargs...)
```

Returns the prediction for the heterogeneous ensemble of models a dataset `X`. The function used to aggregate the outputs from different models is `consensus` (defaults to `median`). All other keyword arguments are passed to `predict`.

To get a direct estimate of the variability, the `consensus` function can be changed to `iqr` (inter-quantile range), or any measure of variance.
