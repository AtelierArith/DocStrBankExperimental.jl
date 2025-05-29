```
nltv(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing,
    Wtv::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing,
    pad::NTuple{3, Integer} = (0, 0, 0),
    Dkernel::Symbol = :k,
    bdir::NTuple{3, Real} = (0, 0, 1),
    lambda::Real = 1e-3,
    rho::Real = 100*lambda,
    mu::Real = 1,
    tol::Real = 1e-3,
    maxit::Integer = 250,
    toln::Real = 1e-6,
    maxitn::Integer = 10,
    verbose::Bool = false,
) -> typeof(similar(f))
```

Nonlinear total variation deconvolution using ADMM [1].

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) local   field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size

### Keywords

  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing`:   data fidelity weights
  * `Wtv::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, 5)}} = nothing`:   total variation weights

      * `M = 3`: same weights for all three gradient directions and all echoes
      * `M = 4 = N`: same weights for all three gradient directions, different weights for echoes
      * `M = 5, (size(Wtv)[4,5] = [1 or N, 3]`: different weights for each gradient direction
  * `pad::NTuple{3, Integer} = (0, 0, 0)`: zero padding array

      * `< 0`: no padding
      * `≥ 0`: minimum padding to fast fft size
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: unit vector of B field direction
  * `Dkernel::Symbol = :k`: dipole kernel method
  * `lambda::Real = 1e-3`: regularization parameter
  * `rho::Real = 100*lambda`: Lagrange multiplier penalty parameter
  * `mu::Real = 1`: Lagrange multiplier penalty parameter (unused if `W = nothing`)
  * `tol::Real = 1e-3`: stopping tolerance
  * `maxit::Integer = 250`: maximum number of iterations
  * `toln::Real = 1e-6`: stopping tolerance for Newton method
  * `maxitn::Integer = 10`: maximum number of iterations for Newton method
  * `verbose::Bool = false`: print convergence information

### Returns

  * `typeof(similar(f))`: susceptibility map

### References

[1] Milovic C, Bilgic B, Zhao B, Acosta‐Cabronero J, Tejos C. Fast nonlinear     susceptibility inversion with variational regularization.     Magnetic resonance in medicine. 2018 Aug;80(2):814-21.
