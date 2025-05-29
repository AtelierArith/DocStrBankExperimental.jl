```
RectLight(color, r::Rect2[, direction = -normal])
RectLight(color, center::Point3f, b1::Vec3f, b2::Vec3f[, direction = -normal])
```

Creates a RectLight with a given color. The first constructor derives the light from a `Rect2` extending in x and y direction. The second specifies the `center` of the rect (or more accurately parallelogram) with `b1` and `b2` specifying the width and height vectors (including scale).

Note that RectLight implements `translate!`, `rotate!` and `scale!` to simplify adjusting the light.

Availability:

  * GLMakie with `Shading = MultiLightShading`
