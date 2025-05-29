```
overbuild(marker, mask; [dims])
overbuild(marker, mask, se)
```

Reconstruction by erosion. This is an alias for [`mreconstruct`](@ref mreconstruct) with `op=erode`.

See also the in-place version [`overbuild!`](@ref), and the dual operator [`underbuild`](@ref).
