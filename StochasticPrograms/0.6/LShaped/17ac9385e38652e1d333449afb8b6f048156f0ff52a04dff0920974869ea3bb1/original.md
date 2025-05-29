```
HybridAggregation
```

Functor object for using hybrid aggregation in an L-shaped algorithm. Create by supplying a [`HybridAggregate`](@ref) object through `aggregate` in `LShaped.Optimizer` or by setting the [`Aggregator`](@ref) attribute.

...

# Parameters

  * `initial::AbstractAggregator`: Initial aggregation scheme
  * `final::AbstractAggregator`: Final aggregation scheme
  * `τ::T`: The active aggregation scheme is switched from `initial` to `final` when the optimality gap decreases below `τ`

...
