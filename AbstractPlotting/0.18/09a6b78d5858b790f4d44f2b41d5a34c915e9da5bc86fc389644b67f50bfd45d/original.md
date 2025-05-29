streamplot(f::function, xinterval, yinterval; kwargs...)

f must either accept `f(::Point)` or `f(x::Number, y::Number)`. f must return a Point2.

Example:

```julia
v(x::Point2{T}) where T = Point2f0(x[2], 4*x[1])
streamplot(v, -2..2, -2..2)
```

## Attributes

Available attributes and their defaults for `AbstractPlotting.StreamPlot` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  arrow_head      AbstractPlotting.Automatic()
  arrow_size      0.03
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color]
  density         1.0
  diffuse         Float32[0.4, 0.4, 0.4]
  gridsize        (32, 32, 32)
  inspectable     true
  lightposition   :eyeposition
  linestyle       "nothing"
  linewidth       1.5
  maxsteps        500
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  quality         16
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  stepsize        0.01
  transparency    false
  visible         true
```

## Implementation

See the function `AbstractPlotting.streamplot_impl` for implementation details.
