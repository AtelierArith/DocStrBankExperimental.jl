```
function getuPressure(::Nothing)
function getuPressure(units)
```

Extract 2D density unit from `units` or `nothing`

## Examples

```jl
julia> getuPressure(nothing)

julia> getuPressure(uAstro)
M⊙ kpc^-1 Gyr^-2

julia> getuPressure(uSI)
kg m^-1 s^-2

julia> getuPressure(uCGS)
g cm^-1 s^-2
```
