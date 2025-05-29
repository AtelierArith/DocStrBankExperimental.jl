```
streamplot(f::function, xinterval, yinterval; color = norm, kwargs...)
```

f must either accept `f(::Point)` or `f(x::Number, y::Number)`. f must return a Point2.

Example:

```julia
v(x::Point2{T}) where T = Point2f(x[2], 4*x[1])
streamplot(v, -2..2, -2..2)
```

One can choose the color of the lines by passing a function `color_func(dx::Point)` to the `color` attribute. By default this is set to `norm`, but can be set to any function or composition of functions. The `dx` which is passed to `color_func` is the output of `f` at the point being colored.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.streamplot}` are: 

```
  alpha           1.0
  arrow_head      MakieCore.Automatic()
  arrow_size      MakieCore.Automatic()
  color           LinearAlgebra.norm
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  density         1.0
  depth_shift     0.0f0
  gridsize        (32, 32, 32)
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  maxsteps        500
  nan_color       :transparent
  overdraw        false
  quality         16
  space           :data
  ssao            false
  stepsize        0.01
  transparency    false
  visible         true
```

## Implementation

See the function `Makie.streamplot_impl` for implementation details.
