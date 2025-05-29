```
gradfp(
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> NTuple{3, typeof(similar(u))}
```

First order forward difference gradient with periodic boundaries.

### Arguments

  * `u::AbstractArray{<:AbstractFloat, 3}`: input array
  * `h::NTuple{3, Real}`: grid spacing

### Returns

  * `dx::typeof(similar(u))`: x-component of gradient of `u`
  * `dy::typeof(similar(u))`: y-component of gradient of `u`
  * `dz::typeof(similar(u))`: z-component of gradient of `u`
