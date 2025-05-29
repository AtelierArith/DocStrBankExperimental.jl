```
resample(f::Function, 
    x::AbstractUncertainValue, y::AbstractUncertainValue,
    n::Int, args...; kwargs...)
```

Draw an `n`-element sample from `x` according to its furnishing distribution, and  draw an `n`-element sample from `y` according to its furnishing distribution. Then, call `f(x_draw, y_draw, args...; kwargs...)` on the length-`n` draws.
