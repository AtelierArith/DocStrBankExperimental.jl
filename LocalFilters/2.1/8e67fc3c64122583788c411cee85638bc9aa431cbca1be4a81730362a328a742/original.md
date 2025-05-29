```
localextrema(A, B=3; order=FORWARD_FILTER) -> Amin, Amax
```

yields the results of performing an erosion and a dilation of `A` by the structuring element defined by `B` in a single pass. Calling this method is usually almost twice as fast as calling [`erode`](@ref) and [`dilate`](@ref).

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

See [`localextrema!`](@ref) for an in-place version of the method, and [`erode`](@ref) or [`dilate`](@ref) for a description of these operations.
