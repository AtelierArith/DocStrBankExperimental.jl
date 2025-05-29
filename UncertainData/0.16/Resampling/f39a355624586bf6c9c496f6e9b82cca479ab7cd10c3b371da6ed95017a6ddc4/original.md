```
resample(f::Function, x::AbstractUncertainValue, n::Int, args...; kwargs...)
```

Draw an `n`-element sample from `x` according to its furnishing distribution, then  call `f(x_draw, args...; kwargs...)` on the length-`n` draws.
