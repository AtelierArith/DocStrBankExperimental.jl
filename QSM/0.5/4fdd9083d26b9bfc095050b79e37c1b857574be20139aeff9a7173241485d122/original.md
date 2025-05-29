```
tsvd(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :k,
    thr::Real = 0.15,
) -> typeof(similar(f))
```

Truncated singular value decomposition (TSVD) [1].

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) local   field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size

### Keywords

  * `pad::NTuple{3, Integer} = (0, 0, 0)`: zero padding array

      * `< 0`: no padding
      * `≥ 0`: minimum padding to fast fft size
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: unit vector of B field direction
  * `Dkernel::Symbol = :k`: dipole kernel method
  * `thr::Real = 0.15`: threshold for k-space filter

### Returns

  * `typeof(similar(f))`: susceptibility map

### References

[1] Wharton S, Schäfer A, Bowtell R. Susceptibility mapping in the human brain     using threshold‐based k‐space division. Magnetic resonance in medicine.     2010 May;63(5):1292-304.
