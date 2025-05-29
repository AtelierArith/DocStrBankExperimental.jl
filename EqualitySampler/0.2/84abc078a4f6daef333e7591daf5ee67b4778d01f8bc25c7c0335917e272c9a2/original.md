```
prediction_rule(d::AbstractPartitionDistribution, r::Integer)
prediction_rule(d::Type{<:AbstractPartitionDistribution}, r::Integer, args...)
```

Compute the prediction rule for a partition distribution, i.e., the probability that a new observations belongs to a new (unseen) cluster. The current number of clusters is given by `r`.
