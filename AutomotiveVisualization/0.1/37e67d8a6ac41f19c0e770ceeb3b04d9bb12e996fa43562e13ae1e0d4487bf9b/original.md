```
TextOverlay
```

Displays some text at the desired location. The coordinates and size units are in pixels by default. The option `coordinate_system` allows to use different units.

# Fields

  * `text::Vector{String}`
  * `color::Colorant = colorant"white"`
  * `font_size::Int = 10`
  * `pos::VecE2 = VecE2(10, font_size)`
  * `line_spacing::Float64 = 1.5` multiple of `font_size`
  * `coordinate_system::Symbol=:camera_pixels`
