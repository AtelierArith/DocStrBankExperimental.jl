```
DynamicAggregate(num_aggregates::Integer, rule::AbstractSelectionRule; lock_after::Function = (τ,n)->false)
```

Factory object for [`DynamicAggregation`](@ref). Pass to `aggregate` in `LShaped.Optimizer` or set the [`Aggregator`](@ref) attribute. See ?DynamicAggregation for parameter descriptions.
