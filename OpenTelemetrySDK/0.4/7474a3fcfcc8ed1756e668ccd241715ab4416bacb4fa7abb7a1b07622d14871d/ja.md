```
HistogramAgg(args...)
```

## 引数:

  * `boundaries::NTuple{M, Float64} where M`、ヒストグラムバケットを計算するための境界。`-Inf` と `Inf` は含めないでください。
  * `is_record_min`
  * `is_record_max`
  * `agg_store`
  * `exemplar_reservoir_factory`、`nothing` に設定されている場合、例示は保存されません。
