```
SpotLight(color, position, direction, angles)
```

Creates a spot light which illuminates objects in a light cone starting at `position` pointing in `direction`. The opening angle is defined by an inner and outer angle given in `angles`, between which the light intensity drops off.

Availability:

  * GLMakie with `shading = MultiLightShading`
  * RPRMakie
