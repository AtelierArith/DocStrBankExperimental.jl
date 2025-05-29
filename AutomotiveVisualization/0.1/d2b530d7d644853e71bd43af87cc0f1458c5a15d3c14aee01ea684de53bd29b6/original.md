```
CameraState(;
    position::VecE2      = VecE2(0.,0.),
    zoom::Real           = 1.,
    rotation::Real       = 0.,
    canvas_width::Int64  = DEFAULT_CANVAS_WIDTH
    canvas_height::Int64 = DEFAULT_CANVAS_HEIGHT
)
```

Representation of the internal camera state.

  * `position::VecE2`: the (x,y) position of the camera in [metre].   The x-direction is measured to the east, y direction to the north.
  * `zoom::Real`: the zoom level of the camera, expressed in [pixels / metre]
  * `rotation::Real`: the rotation angle of the camera in [radian]
  * `canvas_width::Int64`: the canvas width in [pixel]
  * `canvas_height::Int64`: the canvas width in [pixel]
