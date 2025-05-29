```
hg(x, y, z=zero(eltype(x)); θ=zero(eltype(x)), m=0, n=0, w=one(eltype(x)), k=one(eltype(x)))
```

Compute a Hermite-Gaussian mode.

`x`, `y` and `z` can be numbers or vectors, but `x` and `y` must be always of the same kind.

# Other Arguments:

  * `m`: x index
  * `n`: y index
  * `w`: beam's waist
  * `k`: wavenumber

# Examples

```jldoctest
rs = LinRange(-5, 5, 256)
zs = LinRange(0, 1, 32)

# just x and y
ψ₁ = hg(rs, rs, m=3, n=2)
ψ₂ = [hg(x, y, m=3, n=2) for x in rs, y in rs]

# x, y and z
ψ₃ = hg(rs, rs, zs, m=3, n=2)
ψ₄ = [hg(x, y, z, m=3, n=2) for x in rs, y in rs, z ∈ zs]

ψ₁ ≈ ψ₂ && ψ₃ ≈ ψ₄

# output

true
```

See also [`diagonal_hg`](@ref), [`lg`](@ref).
