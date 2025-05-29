```
PointLight(color, position[, attenuation = Vec2f(0)])
PointLight(color, position, range::Real)
```

A point-like light source placed at the given `position` with the given light `color`.

Optionally an attenuation parameter can be used to reduce the brightness of the light source with distance. The reduction is given by `1 / (1 + attenuation[1] * distance + attenuation[2] * distance^2)`. Alternatively you can pass a light `range` to generate matching default attenuation parameters. Note that you may need to set the light intensity, i.e. the light color to values greater than 1 to get satisfying results.

Availability:

  * GLMakie with `shading = MultiLightShading`
  * RPRMakie
