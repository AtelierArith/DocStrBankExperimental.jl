```
lbv(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    atol::Real = sqrt(eps(Float64)),
    rtol::Real = sqrt(eps(Float64)),
    maxit::Integer = maximum(size(f)),
    verbose::Bool = false
) -> typeof(similar(f))
```

Laplacian boundary value problem (LBV) [1].

The Laplacian is computed using second order central finite differences. The resulting Poisson's equation is then solved inside an ROI (`mask`) with homogenous Dirichlet boundary condition (BC) using a multigrid-preconditioned conjugate gradient method. The boundary of the ROI is set such that values outside of it (`mask = 0`) are taken as boundary points and values inside of it (`mask = 1`) as interior points, ie. BC: `fl[!mask] = 0`.

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size

### Keywords

  * `atol::Real = sqrt(eps(Float64))`: absolute stopping tolerance
  * `rtol::Real = sqrt(eps(Float64))`: relative stopping tolerance
  * `maxit::Integer = maximum(size(f))`: maximum number of cg iterations
  * `verbose::Bool = false`: print convergence information

### Returns

  * `typeof(similar(f))`: background corrected local field/phase

### References

[1] Zhou D, Liu T, Spincemaille P, Wang Y. Background field removal by solving     the Laplacian boundary value problem. NMR in Biomedicine. 2014 Mar;27(3):312-9.
