```
calculate_shared_production(::AbstractGroupNC, ECModel::AbstractEC; kwargs...)
```

Calculate the shared produced energy for the Non-Cooperative case. In the Non-Cooperative case, there is no shared energy between users, only self production. Output is normalized with respect to the demand when per_unit is true

''' Outputs –––- shared*en*frac : DenseAxisArray     Shared energy for each user and the aggregation '''
