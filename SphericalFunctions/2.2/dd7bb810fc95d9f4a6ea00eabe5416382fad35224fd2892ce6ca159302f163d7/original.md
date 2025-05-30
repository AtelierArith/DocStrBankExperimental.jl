```
ₛ𝐘(s, ℓₘₐₓ, [T=Float64], [Rθϕ=golden_ratio_spiral_rotors(s, ℓₘₐₓ, T)])
```

Construct a matrix of $ₛYₗₘ(Rθϕ)$ values for the input `s` and all nontrivial $(\ell, m)$ up to `ℓₘₐₓ`.

This is a fast and accurate method for mapping between the vector of spin-weighted spherical-harmonic mode weights $ₛ𝐟ₗₘ$ and the vector of function values on the sphere $ₛ𝐟ⱼₖ$, as

$$
ₛ𝐟ⱼₖ = ₛ𝐘\, ₛ𝐟ₗₘ,
$$

where the right-hand side represents the matrix-vector product.  As usual, we assume that the $ₛ𝐟ₗₘ$ modes are ordered by increasing $m ∈ [-ℓ:ℓ]$, and $ℓ ∈ [|s|:ℓₘₐₓ]$.  The ordering of the $ₛ𝐟ⱼₖ$ values will be determined by the ordering of the argument `Rθϕ`.

Note that the number of modes need not be the same as the number of points on which the function is evaluated, which would imply that the output matrix is not square.  To be able to invert the relationship, however, we need the number of points $ₛ𝐟ⱼₖ$ to be *at least as large* as the number of modes $ₛ𝐟ₗₘ$.

Note that the usefulness of this approach is limited by the fact that the size of this matrix scales as ℓₘₐₓ⁴.  As such, it is mostly useful only for ℓₘₐₓ of order dozens, rather than — say — the tens of thousands that CMB astronomy or lensing require, for example.

Direct application and inversion of this matrix are used in the "direct" methods of $s$-SHT transformations.  See [`SSHTDirect`](@ref) for details about the implementation.
