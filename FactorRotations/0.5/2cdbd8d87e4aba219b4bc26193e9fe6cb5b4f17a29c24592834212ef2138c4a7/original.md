```
isorthogonal(::RotationMethod)
```

Checks if the supplied rotation method is orthogonal.

## Examples

```jldoctest
julia> isorthogonal(Varimax())
true

julia> isorthogonal(Oblimax(orthogonal = false))
false
```
