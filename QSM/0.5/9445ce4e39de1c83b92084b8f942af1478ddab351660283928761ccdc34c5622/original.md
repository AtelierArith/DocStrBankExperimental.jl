```
r2star_ll!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> r2s
```

Log-linear fit.

### Arguments

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2* map (1 / units of TEs)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: multi-echo magnitude
  * `TEs::AbstractVector{<:Real}`: echo times
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest

### Returns

  * `r2s`: R2* map (1 / units of TEs)
