```
gradfp!(
    dx::AbstractArray{<:AbstractFloat, 3},
    dy::AbstractArray{<:AbstractFloat, 3},
    dz::AbstractArray{<:AbstractFloat, 3},
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real},
) -> (dx, dy, dz)
```

First order forward difference gradient with periodic boundaries.

### Arguments

  * `dx::AbstractArray{<:AbstractFloat, 3}`: x-component of gradient of `u`
  * `dy::AbstractArray{<:AbstractFloat, 3}`: y-component of gradient of `u`
  * `dz::AbstractArray{<:AbstractFloat, 3}`: z-component of gradient of `u`
  * `u::AbstractArray{<:AbstractFloat, 3}`: input array
  * `h::NTuple{3, Real}`: grid spacing

### Returns

  * `dx`: x-component of gradient of `u`
  * `dy`: y-component of gradient of `u`
  * `dz`: z-component of gradient of `u`
