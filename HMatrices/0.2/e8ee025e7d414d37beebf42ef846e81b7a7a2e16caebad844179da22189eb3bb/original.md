```
struct CardinalitySplitter <: AbstractSplitter
```

Used to split a `ClusterTree` along the largest dimension if `length(tree)>nmax`. The split is performed so the `data` is evenly distributed amongst all children.

## See also: [`AbstractSplitter`](@ref)
