```
partial_fit(conf_model::TimeSeriesRegressorEnsembleBatch, fitresult, X, y, shift_size)
```

[`TimeSeriesRegressorEnsembleBatch`](@ref) の非適合スコアは、最新のデータ (X,y) によって更新されます。shift_size は、非適合スコアで破棄されるポイントの数を決定します。
