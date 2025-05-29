```
logpdf_model(d::AbstractPartitionDistribution, x::Integer)
logpdf_model(d::AbstractPartitionDistribution, x::AbstractVector{<:Integer})
```

Synonym for `logpdf(d::AbstractPartitionDistribution, x)`, computes the log probability of a partition.
