```
HybridAggregate(initial::AbstractAggregator, final::AbstractAggregator, τ::AbstractFloat)
```

Factory object for [`HybridAggregation`](@ref). Pass to `aggregate` in `LShaped.Optimizer` or by setting the [`Aggregator`](@ref) attribute. See ?HybridAggregation for parameter descriptions.
