```
function getuDensity2D(::Nothing)
function getuDensity2D(units)
```

Extract 2D density unit from `units` or `nothing`

## Examples

```jl
julia> getuDensity2D(nothing)

julia> getuDensity2D(uAstro)
M⊙ kpc^-2

julia> getuDensity2D(uSI)
kg m^-2

julia> getuDensity2D(uCGS)
g cm^-2
```
