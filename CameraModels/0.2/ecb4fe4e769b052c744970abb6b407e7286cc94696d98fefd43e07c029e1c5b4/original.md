```julia
project(model, r_P; c_T_r)

```

Project a world scene onto an image.

Return a transformation that converts real-world coordinates to camera coordinates. This currently ignores any tangential  distortion between the lens and the image plane.

Notes

  * `r_P` is a point in reference frame tranformed the camera's reference frame:

      * `c_P = c_T_r * r_P`

Deprecates:

  * yakir12: `point2pixel`: @deprecate point2pixel(model, pt) project(model, pt[[1;3;2]])

Also see: [`backproject`](@ref)
