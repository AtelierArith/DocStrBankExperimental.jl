```
lg(x, y, z=zero(eltype(x)); p=0, l=0, w=one(eltype(x)), k=one(eltype(x)))
```

Compute a diagonal Hermite-Gaussian mode.

`x`, `y` and `z` can be numbers or vectors, but `x` and `y` must be always of the same kind.

# Other Arguments:

  * `p`: radial index
  * `l`: topological charge
  * `w`: beam's waist
  * `k`: wavenumber

# Examples

```jldoctest
rs = LinRange(-5, 5, 256)
zs = LinRange(0, 1, 32)

# just x and y
ψ₁ = lg(rs, rs, p=1, l=2)
ψ₂ = [lg(x, y, p=1, l=2) for x in rs, y in rs]

# x, y and z
ψ₃ = lg(rs, rs, zs, p=1, l=2)
ψ₄ = [lg(x, y, z, p=1, l=2) for x in rs, y in rs, z ∈ zs]

ψ₃ ≈ ψ₄

# output

true
```

See also [`hg`](@ref), [`diagonal_hg`](@ref).
