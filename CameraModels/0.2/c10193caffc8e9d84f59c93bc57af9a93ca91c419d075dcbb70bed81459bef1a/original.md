```julia
backproject(model, px_coord)

```

Backproject from an image into a world scene.

Return a transformation that converts real-world coordinates to camera coordinates. This currently ignores any tangential  distortion between the lens and the image plane.

Deprecates:

  * yakir12: `pixel2ray`: @deprecate pixel2ray(model, px) backproject(model, px)[[1;3;2]]

Also see: [`project`](@ref)
