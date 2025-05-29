```
DynamicAggregation
```

Functor object for using dynamic aggregation in an L-shaped algorithm. Create by supplying a [`DynamicAggregate`](@ref) object through `aggregate` in `LShaped.Optimizer` or by setting the [`Aggregator`](@ref) attribute.

The following selection rules are available

  * [`SelectUniform`](@ref)
  * [`SelectDecaying`](@ref)
  * [`SelectRandom`](@ref
  * [`SelectClosest`](@ref)
  * [`SortByReference`](@ref)

...

# Parameters

  * `num_aggregates::Int`: Number of aggregates
  * `rule::SelectionRule`: Rule that determines which aggregate an incoming cut should be placed in
  * `lock_after::Function = (τ,n)->false`: Function that determines if the current aggregation scheme should be fixed, based on the current optimality gap `τ` and the number of iterations `n`

...
