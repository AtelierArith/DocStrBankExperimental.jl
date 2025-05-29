```
rotation_type(::RotationMethod)
```

Return the rotation type for a given rotation method.

## Examples

```jldoctest
julia> rotation_type(Varimax())
Orthogonal

julia> rotation_type(Oblimin(gamma = 0.5))
Oblique
```
