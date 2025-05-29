```
density(values; npoints = 200, offset = 0.0, direction = :x)
```

Plot a kernel density estimate of `values`. `npoints` controls the resolution of the estimate, the baseline can be shifted with `offset` and the `direction` set to :x or :y. `bandwidth` and `boundary` are determined automatically by default.

`color` is usually set to a single color, but can also be set to `:x` or `:y` to color with a gradient. If you use `:y` when direction = `:x` (or vice versa), note that only 2-element colormaps can work correctly.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Density` are: 

```
  bandwidth     AbstractPlotting.Automatic()
  boundary      AbstractPlotting.Automatic()
  color         RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  colormap      :viridis
  colorrange    AbstractPlotting.Automatic()
  cycle         [:color => :patchcolor]
  direction     :x
  inspectable   true
  npoints       200
  offset        0.0
  strokearound  false
  strokecolor   :black
  strokewidth   0
```
