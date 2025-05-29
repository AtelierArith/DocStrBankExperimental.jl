```
gradfp_adj!(
    u::AbstractArray{<:AbstractFloat, 3}
    dx::AbstractArray{<:AbstractFloat, 3},
    dy::AbstractArray{<:AbstractFloat, 3},
    dz::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> u
```

Adjoint of first order forward difference gradient with periodic boundaries.

### Arguments

  * `u::AbstractArray{<:AbstractFloat, 3}`: divergence of [dx, dy, dz]
  * `dx::AbstractArray{<:AbstractFloat, 3}`: x-component
  * `dy::AbstractArray{<:AbstractFloat, 3}`: y-component
  * `dz::AbstractArray{<:AbstractFloat, 3}`: z-component
  * `h::NTuple{3, Real}`: grid spacing

### Returns

  * `u`: divergence of [dx, dy, dz]
