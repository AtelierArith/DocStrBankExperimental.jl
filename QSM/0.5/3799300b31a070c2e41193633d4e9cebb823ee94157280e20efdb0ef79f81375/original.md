```
lap!(
    d2u::AbstractArray{<:AbstractFloat, 3},
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> d2u
```

Second order central difference Laplacian.

### Arguments

  * `d2u::AbstractArray{<:AbstractFloat, 3}`: discrete Laplacian of `u`
  * `u::AbstractArray{<:AbstractFloat, 3}`: input array
  * `h::NTuple{3, Real}`: grid spacing

### Returns

  * `d2u`: discrete Laplacian of `u`
