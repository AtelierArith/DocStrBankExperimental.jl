```
multi_echo_linear_fit(
    phas::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real};
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing,
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
    phase_offset::Bool = true
) -> Tuple{typeof(similar(phas)){N-1}, [typeof(similar(phas)){N-1}]}
```

(Weighted) Least squares for multi-echo data.

### Arguments

  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: unwrapped multi-echo phase
  * `TEs::AbstractVector{<:Real}`: echo times

### Keywords

  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing`:   square root of weights, e.g. reciprocal of error variance of voxel   ~> W² = 1/σ²(phas) = mag²/σ²(mag)
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest
  * `phase_offset::Bool = true`: model phase offset (`true`)

### Returns

  * `typeof(similar(phas)){N-1}`: (weighted) least-squares estimate for phase
  * [`typeof(similar(phas)){N-1}`]: (weighted) least-squares estimate for phase offset   if `phase_offset = true`
