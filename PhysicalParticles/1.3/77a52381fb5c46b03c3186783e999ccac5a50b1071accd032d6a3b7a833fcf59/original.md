```
function getuDensity(::Nothing)
function getuDensity(units)
```

Extract 3D density unit from `units` or `nothing`

## Examples

```jl
julia> getuDensity(nothing)

julia> getuDensity(uAstro)
M⊙ kpc^-3

julia> getuDensity(uSI)
kg m^-3

julia> getuDensity(uCGS)
g cm^-3
```
