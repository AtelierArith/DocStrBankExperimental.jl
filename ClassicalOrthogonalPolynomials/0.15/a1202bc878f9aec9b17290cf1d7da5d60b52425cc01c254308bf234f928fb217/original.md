```
legendre(d::AbstractInterval)
```

The [`Legendre`](@ref) polynomials affine-mapped to interval `d`.

# Examples

```jldoctest
julia> P = legendre(0..1)
Legendre() affine mapped to 0 .. 1

julia> axes(P)
(Inclusion(0 .. 1), OneToInf())

julia> P[0.5,:]
ℵ₀-element view(::Legendre{Float64}, 0.0, :) with eltype Float64 with indices OneToInf():
  1.0
  0.0
 -0.5
 -0.0
  0.375
  0.0
 -0.3125
 -0.0
  0.2734375
  0.0
  ⋮
```
