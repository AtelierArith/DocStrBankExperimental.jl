```
waterfall(x, y; kwargs...)
```

Plots a [waterfall chart](https://en.wikipedia.org/wiki/Waterfall_chart) to visualize individual positive and negative components that add up to a net result as a barplot with stacked bars next to each other.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.waterfall}` are: 

```
  cycle            [:color => :patchcolor]
  direction_color  :white
  dodge            MakieCore.Automatic()
  dodge_gap        0.03
  final_color      RGBA{Float64}(0.8980392156862745,0.8980392156862745,0.8980392156862745,0.5)
  final_dodge_gap  0
  final_gap        MakieCore.Automatic()
  gap              0.2
  marker_neg       :dtriangle
  marker_pos       :utriangle
  n_dodge          MakieCore.Automatic()
  show_direction   false
  show_final       false
  stack            MakieCore.Automatic()
  width            MakieCore.Automatic()
```

Furthermore the same attributes as for `barplot` are supported.
