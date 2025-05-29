```
StrictlyMinimumDistance([brute = false,] [metric = Euclidean(),])
```

A distance that can be used in [`set_distance`](@ref). The `StrictlyMinimumDistance` returns the minimum distance of all the distances from a point in one set to the closest point in the other set. The distance is calculated with the given metric.

The `brute::Bool` argument switches the computation between a KDTree-based version, or brute force (i.e., calculation of all distances and picking the smallest one). Brute force performs better for sets that are either large dimensional or have a small amount of points. Deciding a cutting point is not trivial, and is recommended to simply benchmark the [`set_distance`](@ref) function to make a decision.

If `brute = false` this metric only works for `StateSpaceSet`s whose elements are `SVector`s.

For developers: `set_distance` can take a keyword `tree2` that is the KDTree of the second set.
