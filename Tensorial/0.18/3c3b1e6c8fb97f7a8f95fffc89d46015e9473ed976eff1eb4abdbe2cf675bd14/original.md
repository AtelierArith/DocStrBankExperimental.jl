```
cross(x::Vec, y::Vec)
x × y
```

Compute the cross product between two vectors. The infix operation `x × y` (where `×` can be typed by `\times<tab>`) is a synonym for `cross(x, y)`.

# Examples

```jldoctest
julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> y = rand(Vec{3})
3-element Vec{3, Float64}:
 0.8942454282009883
 0.35311164439921205
 0.39425536741585077

julia> x × y
3-element Vec{3, Float64}:
  0.13928086435138393
  0.0669520417303531
 -0.37588028973385323
```
