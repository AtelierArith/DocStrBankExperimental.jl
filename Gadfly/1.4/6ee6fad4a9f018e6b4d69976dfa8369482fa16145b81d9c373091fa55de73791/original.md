```
layer(f::Function, xmin::Number, xmax::Number, ymin::Number, ymax::Number,
      elements::ElementOrFunction...; mapping...) -> [Layers]
```

Create a layer of the contours of the 2D function or expression in `f`. Uses [`Stat.contour`](@ref) for function calculation. See also [`Geom.contour`](@ref).
