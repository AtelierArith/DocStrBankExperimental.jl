```
isoblique(::RotationMethod)
```

Checks if the supplied rotation method is oblique.

## Examples

```jldoctest
julia> isoblique(Varimax())
false

julia> isoblique(Oblimax(orthogonal = false))
true
```
