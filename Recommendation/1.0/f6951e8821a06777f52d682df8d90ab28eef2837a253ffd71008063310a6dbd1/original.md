```
leave_one_out(
    metric::AccuracyMetric,
    recommender_type::Type{<:Recommender},
    data::DataAccessor,
    recommender_args...
)
```

Conduct leave-one-out cross validation (LOOCV) for a combination of recommender `recommender_type` and accuracy metric `metric`. A recommender is initialized with `recommender_args`.
