```
function ismv(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    r::Real = 2*maximum(vsz),
    tol::Real = 1e-3,
    maxit::Integer = 500,
    verbose::Bool = false,
) -> Tuple{typeof(similar(f)), typeof(similar(mask))}
```

Iterative spherical mean value method (iSMV) [1].

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size for smv kernel

### Keywords

  * `r::Real = 2*maximum(vsz)`: radius of smv kernel in units of `vsz`
  * `tol::Real = 1e-3`: stopping tolerance
  * `maxit::Integer = 500`: maximum number of iterations
  * `verbose::Bool = false`: print convergence information

### Returns

  * `typeof(similar(f))`: background corrected local field/phase
  * `typeof(similar(mask))`: eroded binary mask

### References

[1] Wen Y, Zhou D, Liu T, Spincemaille P, Wang Y. An iterative spherical mean     value method for background field removal in MRI.  Magnetic resonance in     medicine. 2014 Oct;72(4):1065-71.
