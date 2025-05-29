```
tikh(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :k,
    lambda::Real = 1e-2,
    reg::Symbol = :gradient
) -> typeof(similar(f))
```

Tikhonov regularization [1].

$$
    argmin_x ||Dx - f||_2^2 + \frac{λ}{2}||Γx||_2^2
$$

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
  * `lambda::Real = 1e-2`: regularization parameter
  * `reg::Symbol = :identity`: regularization matrix Γ   (`:identity`, `:gradient`, `:laplacian`)

### Returns

  * `typeof(similar(f))`: susceptibility map

### References

[1] Bilgic B, Chatnuntawech I, Fan AP, Setsompop K, Cauley SF, Wald LL,     Adalsteinsson E. Fast image reconstruction with L2‐regularization. Journal     of magnetic resonance imaging. 2014 Jul;40(1):181-91.
