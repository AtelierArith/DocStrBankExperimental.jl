```
lap(
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> typeof(similar(u))
```

Second order central difference Laplacian.

### Arguments

  * `u::AbstractArray{<:AbstractFloat, 3}`: input array
  * `h::NTuple{3, Real}`: grid spacing

### Returns

  * `d2u::typeof(similar(u))`: discrete Laplacian of `u`
