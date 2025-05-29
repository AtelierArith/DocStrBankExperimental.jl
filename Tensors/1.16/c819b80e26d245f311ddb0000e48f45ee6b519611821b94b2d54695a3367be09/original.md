```
cross(::Vec, ::Vec)
```

Computes the cross product between two `Vec` vectors, returns a `Vec{3}`. For dimensions 1 and 2 the `Vec`'s are expanded to 3D first. The infix operator `×` (written `\times`) can also be used.

# Examples

```jldoctest
julia> a = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> b = rand(Vec{3})
3-element Vec{3, Float64}:
 0.8942454282009883
 0.35311164439921205
 0.39425536741585077

julia> a × b
3-element Vec{3, Float64}:
  0.13928086435138393
  0.0669520417303531
 -0.37588028973385323
```
