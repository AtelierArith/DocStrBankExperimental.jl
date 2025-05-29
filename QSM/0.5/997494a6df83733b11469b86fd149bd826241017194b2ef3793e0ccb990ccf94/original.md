```
r2star_numart2s!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> r2s
```

Numerical Algorithm for Real-time T2* mapping (NumART2*) [1].

### Arguments

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2* map (1 / units of TEs)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: multi-echo magnitude
  * `TEs::AbstractVector{<:Real}`: echo times
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest

### Returns

  * `r2s`: R2* map (1 / units of TEs)

### References

[1] Hagberg GE, Indovina I, Sanes JN, Posse S. Real‐time quantification of T2*     changes using multiecho planar imaging and numerical methods.     Magnetic Resonance in Medicine: An Official Journal of the International     Society for Magnetic Resonance in Medicine. 2002 Nov;48(5):877-82.
