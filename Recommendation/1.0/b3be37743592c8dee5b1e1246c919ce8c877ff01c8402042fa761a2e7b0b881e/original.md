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

Conduct `n_folds` cross validation for a combination of recommender `recommender_type` and ranking metric `metric`. A recommender is initialized with `recommender_args` and runs top-`k` recommendation.
