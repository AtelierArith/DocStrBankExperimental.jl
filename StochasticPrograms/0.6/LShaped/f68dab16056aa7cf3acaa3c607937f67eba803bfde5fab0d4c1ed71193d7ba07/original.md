```
ClusterAggregate(rule::AbstractClusterRule; lock_after::Function = (τ,n)->false)
```

Factory object for [`ClusterAggregation`](@ref). Pass to `aggregate` in `LShaped.Optimizer` or set the [`Aggregator`](@ref) attribute. See ?ClusterAggregation for parameter descriptions.
