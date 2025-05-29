```
mSpinArray(dim::Dims; T1=1.47u"s", T2=0.07u"s", γ=γ¹H, M=[0. 0. 1.])
mSpinArray(mask::BitArray; T1=1.47u"s", T2=0.07u"s", γ=γ¹H, M=[0. 0. 1.])
```

An exemplary struct instantiating `AbstractSpinArray`.

# Fields:

*Immutable*:

  * `dim::Dims` (nd,): `nM ← prod(dim)`, dimension of the object.
  * `mask::BitArray` (nx,(ny,(nz))): Mask for `M`, `dim == (nx,(ny,(nz)))`

*Mutable*:

  * `T1::TypeND(T0D, [0,1])` (1,) or (nM,): Longitudinal relaxation coeff.
  * `T2::TypeND(T0D, [0,1])` (1,) or (nM,): Transversal relaxation coeff.
  * `γ::TypeND(Γ0D, [0,1])`  (1,) or (nM,): Gyromagnetic ratio.
  * `M::TypeND(Real, [2])`   (`count(mask)`, 3):  Magnetic spins, (𝑀x,𝑀y,𝑀z).

# Notes:

off-resonance, `Δf`, and locations, `loc`, are intentionally unincluded, as they are not intrinsic to spins, and can change over time. Unincluding them allows extensional subtypes specialized for, e.g., arterial spin labelling.

See also: [`AbstractSpinArray`](@ref).
