```
r2star_numart2s(
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> typeof(similar(mag, size(mag)[1:N-1]))
```

Numerical Algorithm for Real-time T2* mapping (NumART2*) [1].

### Arguments

  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: multi-echo magnitude
  * `TEs::AbstractVector{<:Real}`: echo times
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest

### Returns

  * `typeof(similar(mag, size(mag)[1:N-1]))`: R2* map (1 / units of TEs)

### References

[1] Hagberg GE, Indovina I, Sanes JN, Posse S. Real‐time quantification of T2*     changes using multiecho planar imaging and numerical methods.     Magnetic Resonance in Medicine: An Official Journal of the International     Society for Magnetic Resonance in Medicine. 2002 Nov;48(5):877-82.
