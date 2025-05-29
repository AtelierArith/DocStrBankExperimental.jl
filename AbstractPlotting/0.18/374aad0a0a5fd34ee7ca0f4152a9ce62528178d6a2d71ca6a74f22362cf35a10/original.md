```
update_limits!(scene::Scene, new_limits::Rect, padding = Vec3f0(0))
```

This function updates the limits of the given `Scene` according to the given Rect.

A `Rect` is a generalization of a rectangle to n dimensions.  It contains two vectors. The first vector defines the origin; the second defines the displacement of the vertices from the origin. This second vector can be thought of in two dimensions as a vector of width (x-axis) and height (y-axis), and in three dimensions as a vector of the width (x-axis), breadth (y-axis), and height (z-axis).

Such a `Rect` can be constructed using the `FRect` or `FRect3D` functions that are exported by `AbstractPlotting.jl`.  See their documentation for more information.
