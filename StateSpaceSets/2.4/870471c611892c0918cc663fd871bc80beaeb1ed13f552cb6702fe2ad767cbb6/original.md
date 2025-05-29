```
Hausdorff(metric = Euclidean())
```

A distance that can be used in [`set_distance`](@ref). The [Hausdorff distance](https://en.wikipedia.org/wiki/Hausdorff_distance) is the greatest of all the distances from a point in one set to the closest point in the other set. The distance is calculated with the metric given to `Hausdorff` which defaults to Euclidean.

`Hausdorff` is 2x slower than [`StrictlyMinimumDistance`](@ref), however it is a proper metric in the space of sets of state space sets.

This metric only works for `StateSpaceSet`s whose elements are `SVector`s.

For developers: `set_distance` can take keywords `tree1, tree2` that are the KDTrees of the first and second sets respectively.
