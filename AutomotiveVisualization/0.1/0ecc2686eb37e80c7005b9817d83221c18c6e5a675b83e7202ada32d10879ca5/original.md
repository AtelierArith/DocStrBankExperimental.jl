```
IDOverlay
```

Display the ID on top of each entity in a scene. The text can be customized with the `color::Colorant` (default=white) and `font_size::Int64` (default=15) keywords. The position of the ID can be adjusted using `x_off::Float64` and `y_off::Float64` (in camera coordinates).

# Fields

  * `color::Colorant = colorant"white"`
  * `font_size::Int = 15`
  * `x_off::Float64 = 0.`
  * `y_off::Float64 = 0.`
