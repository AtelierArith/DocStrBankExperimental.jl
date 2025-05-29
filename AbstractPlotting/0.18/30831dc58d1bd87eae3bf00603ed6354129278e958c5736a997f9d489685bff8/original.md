streamplot(f::function, xinterval, yinterval; kwargs...)

f must either accept `f(::Point)` or `f(x::Number, y::Number)`. f must return a Point2.

Example:

```julia
v(x::Point2{T}) where T = Point2f0(x[2], 4*x[1])
streamplot(v, -2..2, -2..2)
```

## Attributes

Available attributes and their defaults for `AbstractPlotting.Combined{AbstractPlotting.streamplot!}` are: 

```

```

## Implementation

See the function `AbstractPlotting.streamplot_impl` for implementation details.
