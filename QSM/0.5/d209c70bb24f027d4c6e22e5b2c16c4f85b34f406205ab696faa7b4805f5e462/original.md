```
rts(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    Dkernel::Symbol = :k,
    bdir::NTuple{3, Real} = (0, 0, 1),
    lstol::Integer = 4,
    delta::Real = 0.15,
    mu::Real = 1e5,
    rho::Real = 10,
    tol::Real = 1e-2,
    maxit::Integer = 20,
    verbose::Bool = false,
) -> typeof(similar(f))
```

Rapid two-step dipole inversion with sparsity priors [1].

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
  * `lstol::Integer = 4`: stopping tolerance (# of iterations) for lsmr solver
  * `delta::Real = 0.15`: threshold for ill-conditioned k-space region
  * `mu::Real = 1e5`: regularization parameter for tv minimization
  * `rho::Real = 10`: Lagrange multiplier penalty parameter
  * `tol::Real = 1e-2`: stopping tolerance
  * `maxit::Integer = 20`: maximum number of iterations
  * `verbose::Bool = false`: print convergence information

### Returns

  * `typeof(similar(f))`: susceptibility map

### References

[1] Kames C, Wiggermann V, Rauscher A. Rapid two-step dipole inversion for     susceptibility mapping with sparsity priors.     Neuroimage. 2018 Feb 15;167:276-83.
