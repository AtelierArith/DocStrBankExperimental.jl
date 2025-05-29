```
NestedPowerRepresentation
```

Representation of points and tangent vectors on a power manifold using arrays of size equal to `TSize` of a [`PowerManifold`](@ref). Each element of such array stores a single point or tangent vector.

For modifying operations, each element of the outer array is modified in-place, differently than in [`NestedReplacingPowerRepresentation`](@ref).
