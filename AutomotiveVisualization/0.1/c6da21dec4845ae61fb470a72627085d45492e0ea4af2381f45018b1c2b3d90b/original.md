```
NeighborsOverlay
```

Draws a line between a vehicle and its neighbors. The neighbors are linked with different colors depending on their lanes.

# Fields

  * `target_id::Int`
  * `color_L::Colorant = colorant"blue"`
  * `color_M::Colorant = colorant"green`
  * `color_R::Colorant = colorant"red"`
  * `line_width::Float64 = 0.5`
  * `textparams::TextParams = TextParams()`
