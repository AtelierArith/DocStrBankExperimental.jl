```
HistogramOverlay
```

Display a bar at the specified position `pos`, the bar is of size `width`, `height` and is filled up to a given proportion of its height. The fill proportion is set using `val`, it should be a number between 0 and 1. If it is 0, the bar is not filled, if it is 1 it is filled to the top.

# Fields

  * `pos::VecE2{Float64} = VecE2(0.,0.)`
  * `coordinate_system::Symbol = :scene`
  * `label::String = "histogram"`
  * `val::Float64 = 0.5` should be between 0 and 1
  * `width::Float64 = 2.`
  * `height::Float64 = 5.`
  * `fill_color::Colorant = colorant"blue"`
  * `line_color::Colorant = colorant"white"`
  * `font_size::Int64 = 15 # [pix]`
  * `label_pos::VecSE2{Float64} = pos + VecSE2(0., -height/2)` position of the label
