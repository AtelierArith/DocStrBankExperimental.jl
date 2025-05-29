```
cross_validation(
    n_folds::Integer,
    metric::AccuracyMetric,
    recommender_type::Type{<:Recommender},
    data::DataAccessor,
    recommender_args...
)
```

Conduct `n_folds` cross validation for a combination of recommender `recommender_type` and accuracy metric `metric`. A recommender is initialized with `recommender_args`.
