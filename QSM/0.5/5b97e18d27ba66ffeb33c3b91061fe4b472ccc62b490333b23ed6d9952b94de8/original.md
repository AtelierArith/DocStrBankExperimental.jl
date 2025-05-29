```
crop_mask(
    x::AbstractArray,
    m::AbstractArray = x;
    out = 0
) -> typeof(x[...])
```

Crop array to mask.

### Arguments

  * `x::AbstractArray`: array to be cropped
  * `m::AbstractArray`: mask

### Keywords

  * `out = 0`: value in `m` considered outside

### Returns

  * `typeof(x[...])`: cropped array
