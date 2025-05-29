```
vsharp(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    r::AbstractVector{<:Real} = 18*minimum(vsz):-2*maximum(vsz):2*maximum(vsz),
    thr::Real = 0.05,
) -> Tuple{typeof(similar(f)), typeof(similar(mask))}
```

Variable kernels sophisticated harmonic artifact reduction for phase data (V-SHARP) [1].

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size for smv kernel

### Keywords

  * `r::AbstractVector{<:Real} = 18*minimum(vsz):-2*maximum(vsz):2*maximum(vsz)`:   radii of smv kernels in mm
  * `thr::Real = 0.05`: threshold for high pass filter

### Returns

  * `typeof(similar(f))`: background corrected local field/phase
  * `typeof(similar(mask))`: eroded binary mask

### References

[1] Wu B, Li W, Guidon A, Liu C. Whole brain susceptibility mapping using     compressed sensing. Magnetic resonance in medicine. 2012 Jan;67(1):137-47.
