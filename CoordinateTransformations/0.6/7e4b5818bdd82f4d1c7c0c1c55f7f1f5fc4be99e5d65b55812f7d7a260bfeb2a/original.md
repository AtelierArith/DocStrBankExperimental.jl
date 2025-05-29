```
PerspectiveMap()
```

Construct a perspective transformation. The perspective transformation takes, e.g., a point in 3D space and "projects" it onto a 2D virtual screen of an ideal pinhole camera (at distance `1` away from the camera). The camera is oriented towards the positive-Z axis (or in general, along the final dimension) and the sign of the `x` and `y` components is preserved for objects in front of the camera (objects behind the camera are also projected and therefore inverted - it is up to the user to cull these as necessary).

This transformation is designed to be used in composition with other coordinate transformations, defining e.g. the position and orientation of the camera. For example:

```julia
cam_transform = PerspectiveMap() ∘ inv(AffineMap(cam_rotation, cam_position))
screen_points = map(cam_transform, points)
```

(see also [`cameramap`](@ref))
