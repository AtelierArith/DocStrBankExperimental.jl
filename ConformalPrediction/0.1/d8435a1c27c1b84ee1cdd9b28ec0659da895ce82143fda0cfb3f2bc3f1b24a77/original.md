```
partial_fit(conf_model::TimeSeriesRegressorEnsembleBatch, fitresult, X, y, shift_size)
```

For the [`TimeSeriesRegressorEnsembleBatch`](@ref) Non-conformity scores are updated by the most recent data (X,y). shift_size determines how many points in Non-conformity scores will be discarded.
