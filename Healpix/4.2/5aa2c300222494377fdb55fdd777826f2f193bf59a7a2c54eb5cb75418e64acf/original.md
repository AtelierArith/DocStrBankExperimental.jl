```
gnomonic(m::HealpixMap{T, O, AA}, projparams = Dict()) where {T <: Number, O, AA}
```

High-level wrapper around `project` for gnomonic projections.

The following parameters can be set in the `projparams` dictionary:

  * `width`: width of the image, in pixels (default: 720 pixels)
  * `height`: height of the image, in pixels; if not specified, it will be assumed to be equal to `width`
  * `center`: position and orientation of the pixel in the middle. It is a 3-element tuple containing:

    1. The *latitude* of the pixel, in radians
    2. The longitude of the pixel, in radians
    3. The rotation to be applied to the image, in radians
  * `fov_rad`: size of the image along the x and y axes, in radians (default: 15°)

# Example

```julia
plot(m, gnomonic, Dict(:fov_rad = deg2rad(1.5), :center = (0, 0, deg2rad(45))))
```
