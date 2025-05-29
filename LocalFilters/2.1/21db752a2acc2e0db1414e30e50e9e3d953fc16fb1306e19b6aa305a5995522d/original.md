```
localextrema!(Amin, Amax, A, B=3; order=FORWARD_FILTER) -> Amin, Amax
```

overwrites `Amin` and `Amax` with, respectively, an erosion and a dilation of the array `A` by the structuring element defined by `B` in a single pass.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

See [`localextrema`](@ref) for an out-of-place version for more information.
