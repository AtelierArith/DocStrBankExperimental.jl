```
TriclinicBoundary(v1, v2, v3; approx_images=true)
TriclinicBoundary(SVector(v1, v2, v3); approx_images=true)
TriclinicBoundary(SVector(l1, l2, l3), SVector(α, β, γ); approx_images=true)
TriclinicBoundary(arr; approx_images=true)
```

Triclinic 3D bounding box defined by 3 `SVector{3}` basis vectors or basis vector lengths and angles α/β/γ in radians.

The first basis vector must point along the x-axis and the second must lie in the xy plane. An approximation is used to find the closest periodic image when using the minimum image convention. The approximation is correct for distances shorter than half the shortest box height/width. Setting the keyword argument `approx_images` to `false` means the exact closest image is found, which is slower.

Not currently able to simulate a cubic box, use [`CubicBoundary`](@ref) or small offsets instead. Not currently compatible with infinite boundaries.
