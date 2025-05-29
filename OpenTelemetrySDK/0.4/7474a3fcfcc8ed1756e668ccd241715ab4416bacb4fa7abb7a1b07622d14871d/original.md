```
HistogramAgg(args...)
```

## Arguments:

  * `boundaries::NTuple{M, Float64} where M`, the boundaries to calculate histogram buckets. Note that `-Inf` and `Inf` shouldn't be included.
  * `is_record_min`
  * `is_record_max`
  * `agg_store`
  * `exemplar_reservoir_factory`, when set to `nothing`, no exemplar will be stored.
