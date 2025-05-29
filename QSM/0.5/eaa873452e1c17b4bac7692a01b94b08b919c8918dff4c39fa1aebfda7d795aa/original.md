```
erode_mask!(
    emask::AbstractArray{Bool, 3},
    mask::AbstractArray{Bool, 3},
    iter::Integer = 1
) -> emask
```

Erode binary mask using an 18-stencil cube.

### Arguments

  * `emask::AbstractArray{Bool, 3}`: eroded binary mask
  * `mask::AbstractArray{Bool, 3}`: binary mask
  * `iter::Integer = 1`: erode `iter` times

### Returns

  * `emask`: eroded binary mask
