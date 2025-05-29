```
movefocus(target)
```

Rotate the camera view axis, moving the focus to the `target` point.

This only affects 3-D scenes created with camera settings, e.g. [`isosurface`](@ref) plots. Moving the focus point rotates the camera without changing its position; in order to rotate the camera around the center of the scene, use the functions [`rotate`](@ref), [`tilt`](@ref) or [`viewpoint`](@ref).

# Examples

```julia
# Move the focus to the point (1.0, 0.5, 0.0)
movefocus([1.0, 0.5, 0.0])
```
