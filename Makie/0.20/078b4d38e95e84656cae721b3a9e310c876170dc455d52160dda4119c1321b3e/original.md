```
barplot(x, y; kwargs...)
```

Plots a barplot; `y` defines the height. `x` and `y` should be 1 dimensional. Bar width is determined by the attribute `width`, shrunk by `gap` in the following way: `width -> width * (1 - gap)`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.barplot}` are: 

```
  alpha                  1.0
  bar_labels             "nothing"
  color                  RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  color_over_background  MakieCore.Automatic()
  color_over_bar         MakieCore.Automatic()
  colormap               :viridis
  colorrange             MakieCore.Automatic()
  colorscale             identity
  cycle                  [:color => :patchcolor]
  direction              :y
  dodge                  MakieCore.Automatic()
  dodge_gap              0.03
  fillto                 MakieCore.Automatic()
  flip_labels_at         Inf
  gap                    0.2
  highclip               MakieCore.Automatic()
  inspectable            true
  label_align            MakieCore.Automatic()
  label_color            :black
  label_font             :regular
  label_formatter        Makie.bar_label_formatter
  label_offset           5
  label_rotation         0.0
  label_size             14
  lowclip                MakieCore.Automatic()
  marker                 GeometryBasics.HyperRectangle
  n_dodge                MakieCore.Automatic()
  nan_color              :transparent
  offset                 0.0
  stack                  MakieCore.Automatic()
  strokecolor            :black
  strokewidth            0
  transparency           false
  visible                true
  width                  MakieCore.Automatic()
```
