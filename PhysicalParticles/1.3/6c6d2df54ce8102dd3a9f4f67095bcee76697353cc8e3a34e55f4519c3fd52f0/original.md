```
function datadimension
```

Traits function to specify whether the data is unitful/unitless and 2D/3D.

## Examples

```jl
julia> datadimension(PVector2D())
Unitless2D()

julia> datadimension(PVector())
Unitless3D()

julia> datadimension(Star2D(uAstro))
Physical2D()

julia> datadimension(Star(uAstro))
Physical3D()

julia> datadimension([PVector2D()])
Unitless2D()

julia> datadimension([PVector()])
Unitless3D()

julia> datadimension([Star2D(uAstro)])
Physical2D()

julia> datadimension([Star(uAstro)])
Physical3D()
```
