```
cross_validation(
    n_folds::Integer,
    metric::Union{RankingMetric, AggregatedMetric, Coverage, Novelty},
    topk::Integer,
    recommender_type::Type{<:Recommender},
    data::DataAccessor,
    recommender_args...;
    allow_repeat::Bool=false
)
```

`n_folds` の交差検証を、レコメンダー `recommender_type` とランキングメトリック `metric` の組み合わせに対して実施します。レコメンダーは `recommender_args` で初期化され、トップ `k` の推薦を実行します。
