```
leave_one_out(
    metric::AccuracyMetric,
    recommender_type::Type{<:Recommender},
    data::DataAccessor,
    recommender_args...
)
```

レーブワンアウト交差検証（LOOCV）を、レコメンダー `recommender_type` と精度指標 `metric` の組み合わせに対して実施します。レコメンダーは `recommender_args` で初期化されます。
