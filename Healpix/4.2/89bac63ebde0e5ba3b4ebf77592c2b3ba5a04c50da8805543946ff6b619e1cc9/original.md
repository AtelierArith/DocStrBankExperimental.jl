```
mollweide(m::HealpixMap{T, O, AA}, projparams = Dict()) where {T <: Number, O, AA}
```

High-level wrapper around `project` for Mollweide projections.

The following parameters can be set in the `projparams` dictionary:

  * `width`: width of the image, in pixels (default: 720 pixels)
  * `height`: height of the image, in pixels; if not specified, it will be assumed to be equal to `width`
