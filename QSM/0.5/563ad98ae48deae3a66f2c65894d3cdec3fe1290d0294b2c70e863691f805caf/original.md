```
gradfp_adj(
    dx::AbstractArray{<:AbstractFloat, 3},
    dy::AbstractArray{<:AbstractFloat, 3},
    dz::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> typeof(similar(dx, promote_eltype(dx, dy, dz)))
```

Adjoint of first order forward difference gradient with periodic boundaries.

### Arguments

  * `dx::AbstractArray{<:AbstractFloat, 3}`: x-component
  * `dy::AbstractArray{<:AbstractFloat, 3}`: y-component
  * `dz::AbstractArray{<:AbstractFloat, 3}`: z-component
  * `h::NTuple{3, Real}`: grid spacing

### Returns

  * `u::typeof(similar(dx, promote_eltype(dx, dy ,dz)))`: divergence of [dx, dy, dz]
