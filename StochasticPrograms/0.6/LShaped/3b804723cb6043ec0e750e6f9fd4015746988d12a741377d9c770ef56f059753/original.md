```
ClusterAggregation
```

Functor object for using cluster aggregation in an L-shaped algorithm. Create by supplying a [`ClusterAggregate`](@ref) object through `aggregate` in `LShaped.Optimizer` or by setting the [`Aggregator`](@ref) attribute.

The following cluster rules are available

  * [`StaticCluster`](@ref)
  * [`ClusterByReference`](@ref)
  * [`Kmedoids`](@ref
  * [`Hierarchical`](@ref)

...

# Parameters

  * `rule::ClusterRule`: Rule that determines how cuts should be sorted into clusters
  * `lock_after::Function = (τ,n)->false`: Function that determines if the current aggregation scheme should be fixed, based on the current optimality gap `τ` and the number of iterations `n`

...
