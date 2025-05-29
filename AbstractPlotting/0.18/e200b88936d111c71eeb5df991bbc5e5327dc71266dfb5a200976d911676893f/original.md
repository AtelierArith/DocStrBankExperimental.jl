```
barplot(x, y; kwargs...)
```

Plots a barplot; `y` defines the height.  `x` and `y` should be 1 dimensional.

## Attributes

Available attributes and their defaults for `AbstractPlotting.BarPlot` are: 

```
  color        RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  colormap     :viridis
  colorrange   AbstractPlotting.Automatic()
  cycle        [:color => :patchcolor]
  direction    :y
  dodge        AbstractPlotting.Automatic()
  dodge_gap    0.03
  fillto       AbstractPlotting.Automatic()
  inspectable  true
  marker       GeometryBasics.HyperRectangle
  n_dodge      AbstractPlotting.Automatic()
  stack        AbstractPlotting.Automatic()
  strokecolor  :black
  strokewidth  0
  visible      true
  width        AbstractPlotting.Automatic()
  x_gap        0.2
```
