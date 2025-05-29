```
erode_mask(mask::AbstractArray{Bool, 3}, iter::Integer = 1) -> typeof(similar(mask))
```

Erode binary mask using an 18-stencil cube.

### Arguments

  * `mask::AbstractArray{Bool, 3}`: binary mask
  * `iter::Integer = 1`: erode `iter` times

### Returns

  * `typeof(similar(mask))`: eroded binary mask
