```
unwrap_laplacian(
    phas::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    solver::Symbol = :mgpcg
) -> typeof(similar(phas))
```

Laplacian phase unwrapping [1].

The Laplacian is computed using second order central finite differences on the complex phase. The resulting Poisson's equation can be solved with homogeneous Dirichlet (`solver = :mgpcg`), Neumann (`:dct`), or periodic (`:fft`) boundary conditions (BCs). Neumann and periodic BCs are imposed on the array while Dirichlet BCs are imposed on a region-of-interest (ROI) (`mask`). The boundary of the ROI is set such that values outside of it (`mask = 0`) are taken as boundary points and values inside of it (`mask = 1`) as interior points, ie. BC: `uphas[!mask] = 0`. This method combines phase unwrapping [1] and harmonic background field removing [2].

### Arguments

  * `phas::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: wrapped (multi-echo) phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size

### Keywords

  * `solver::Symbol = :mgpcg`: solver for Poisson equation

      * `:dct`: homogeneous Neumann boundary condition on array
      * `:fft`: periodic boundary condition on array
      * `:mgpcg`: homogeneous Dirichlet boundary condition on `mask`   (multigrid-preconditioned conjugate gradient method)

### Returns

  * `typeof(similar(phas))`: unwrapped phase

### References

[1] Schofield MA, Zhu Y. Fast phase unwrapping algorithm for interferometric     applications. Optics letters. 2003 Jul 15;28(14):1194-6.

[2] Zhou D, Liu T, Spincemaille P, Wang Y. Background field removal by solving     the Laplacian boundary value problem. NMR in Biomedicine. 2014 Mar;27(3):312-9.
