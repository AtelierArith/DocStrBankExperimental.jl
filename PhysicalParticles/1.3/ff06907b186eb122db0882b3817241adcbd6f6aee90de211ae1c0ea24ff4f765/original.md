```
function getuEnergyUnit(::Nothing)
function getuEnergyUnit(units)
```

Extract energy per mass unit from `units` or `nothing`

## Examples

```jl
julia> getuEnergyUnit(nothing)

julia> getuEnergyUnit(uAstro)
kpc^2 Gyr^-2

julia> getuEnergyUnit(uSI)
m^2 s^-2

julia> getuEnergyUnit(uCGS)
cm^2 s^-2
```
