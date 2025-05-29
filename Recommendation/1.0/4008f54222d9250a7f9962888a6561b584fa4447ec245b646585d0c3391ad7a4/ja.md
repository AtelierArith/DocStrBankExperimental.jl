```
cross_validation(
    n_folds::Integer,
    metric::AccuracyMetric,
    recommender_type::Type{<:Recommender},
    data::DataAccessor,
    recommender_args...
)
```

`n_folds` の交差検証を、レコメンダー `recommender_type` と精度メトリック `metric` の組み合わせに対して実施します。レコメンダーは `recommender_args` で初期化されます。
