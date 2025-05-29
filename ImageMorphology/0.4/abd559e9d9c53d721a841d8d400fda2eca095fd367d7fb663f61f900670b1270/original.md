```
underbuild(marker, mask; [dims])
underbuild(marker, mask, se)
```

Reconstruction by dilation. This is an alias for [`mreconstruct`](@ref mreconstruct) with `op=dilate`.

See also the in-place version [`underbuild!`](@ref), and the dual operator [`overbuild`](@ref).
