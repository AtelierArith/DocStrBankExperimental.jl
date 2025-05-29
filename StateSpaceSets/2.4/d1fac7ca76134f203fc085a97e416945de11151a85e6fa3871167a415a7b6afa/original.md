```
set_distance(ssset1, ssset2 [, distance])
```

Calculate a distance between two `StateSpaceSet`s, i.e., a distance defined between sets of points, as dictated by `distance`.

Possible `distance` types are:

  * [`Centroid`](@ref), which is the default, and 100s of times faster than the rest
  * [`Hausdorff`](@ref)
  * [`StrictlyMinimumDistance`](@ref)
  * Any function `f(A, B)` that returns the distance between two state space sets `A, B`.
