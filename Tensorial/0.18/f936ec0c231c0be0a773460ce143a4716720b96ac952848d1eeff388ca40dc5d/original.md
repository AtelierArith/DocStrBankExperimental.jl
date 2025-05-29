```
vol(::AbstractVec{3})
```

Compute the volumetric part of a vector (assuming principal values of stresses and strains). This is only available in 3D.

# Examples

```jldoctest
julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> vol(x)
3-element Vec{3, Float64}:
 0.3645381733326641
 0.3645381733326641
 0.3645381733326641

julia> vol(x) + dev(x) ≈ x
true
```
