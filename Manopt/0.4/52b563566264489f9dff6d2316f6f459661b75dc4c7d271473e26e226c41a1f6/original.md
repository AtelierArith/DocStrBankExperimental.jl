```
get_cost(M::AbstractManifold, mco::AbstractManifoldCostObjective, p)
```

Evaluate the cost function from within the [`AbstractManifoldCostObjective`](@ref) on `M` at `p`.

By default this implementation assumed that the cost is stored within `mco.cost`.
