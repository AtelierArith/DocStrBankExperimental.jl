```
r2star_arlo(
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> typeof(similar(mag, size(mag)[1:N-1]))
```

Auto-Regression on Linear Operations (ARLO) [1].

### Arguments

  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: multi-echo magnitude
  * `TEs::AbstractVector{<:Real}`: echo times
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest

### Returns

  * `typeof(similar(mag, size(mag)[1:N-1]))`: R2* map (1 / units of TEs)

### References

[1] Pei M, Nguyen TD, Thimmappa ND, Salustri C, Dong F, Cooper MA, Li J,     Prince MR, Wang Y. Algorithm for fast monoexponential fitting based on     auto‐regression on linear operations (ARLO) of data.     Magnetic resonance in medicine. 2015 Feb;73(2):843-50.
