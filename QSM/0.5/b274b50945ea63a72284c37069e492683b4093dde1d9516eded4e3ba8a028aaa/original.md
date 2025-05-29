```
pdf(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing,
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :i,
    lambda::Real = 0,
    tol::Real = 1e-5,
    maxit::Integer = ceil(sqrt(numel(mask))),
    verbose::Bool = false
) -> typeof(similar(f))
```

Projection onto dipole fields (PDF) [1].

### Arguments

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: unwrapped (multi-echo) field/phase
  * `mask::AbstractArray{Bool, 3}`: binary mask of region of interest
  * `vsz::NTuple{3, Real}`: voxel size for dipole kernel

### Keywords

  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing`:   data fidelity weights
  * `pad::NTuple{3, Integer} = (0, 0, 0)`: zero padding array

      * `< 0`: no padding
      * `≥ 0`: minimum padding to fast fft size
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: unit vector of B field direction
  * `Dkernel::Symbol = :i`: dipole kernel method
  * `lambda::Real = 0`: regularization parameter
  * `tol::Real = 1e-5`: stopping tolerance for iterative solver
  * `maxit::Integer = ceil(sqrt(length(mask)))`: maximum number of iterations for   iterative solver
  * `verbose::Bool = false`: print convergence information

### Returns

  * `typeof(similar(f))`: background corrected local field/phase

### References

[1] Liu T, Khalidov I, de Rochefort L, Spincemaille P, Liu J, Tsiouris AJ,     Wang Y. A novel background field removal method for MRI using projection     onto dipole fields. NMR in Biomedicine. 2011 Nov;24(9):1129-36.
