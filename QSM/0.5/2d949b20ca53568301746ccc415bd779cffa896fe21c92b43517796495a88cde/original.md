```
crop_indices(x::AbstractArray, out = 0) -> CartesianIndices
```

Indices to crop mask.

### Arguments

  * `x::AbstractArray`: mask
  * `out = 0`: value in `x` considered outside

### Returns

  * `CartesianIndices`: indices to crop mask
