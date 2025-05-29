```
orthographic(m::HealpixMap{T,O}, projparams = Dict()) where {T <: Number,O <: Order}
```

High-level wrapper around `project` for orthographic projections.

The following parameters can be set in the `projparams` dictionary:

  * `width`: width of the image, in pixels (default: 720 pixels)
  * `height`: height of the image, in pixels; if not specified, it will be assumed to be equal to `width`
  * `center`: position of the pixel in the middle of the left globe (*latitude* and longitude).
