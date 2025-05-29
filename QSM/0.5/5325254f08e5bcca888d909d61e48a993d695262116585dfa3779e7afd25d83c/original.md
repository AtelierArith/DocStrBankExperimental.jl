```
sharp(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    r::Real = 18*minimum(vsz),
    thr::Real = 0.05,
) -> Tuple{typeof(similar(f)), typeof(similar(mask))}
```

Sophisticated harmonic artifact reduction for phase data (SHARP) [1].

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size for smv kernel

### Keywords

  * `r::Real = 18*minimum(vsz)`: radius of smv kernel in units of `vsz`
  * `thr::Real = 0.05`: threshold for high pass filter

### Returns

  * `typeof(similar(f))`: background corrected local field/phase
  * `typeof(similar(mask))`: eroded binary mask

### References

[1] Schweser F, Deistung A, Lehr BW, Reichenbach JR. Quantitative imaging of     intrinsic magnetic tissue properties using MRI signal phase: an approach to     in vivo brain iron metabolism?. Neuroimage. 2011 Feb 14;54(4):2789-807.
