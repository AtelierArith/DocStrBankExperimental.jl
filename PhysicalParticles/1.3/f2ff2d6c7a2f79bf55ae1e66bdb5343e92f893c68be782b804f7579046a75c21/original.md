```
function getuEnergy(::Nothing)
function getuEnergy(units)
```

Extract energy unit from `units` or `nothing`

## Examples

```jl
julia> getuEnergy(nothing)

julia> getuEnergy(uAstro)
kpc^2 M⊙ Gyr^-2

julia> getuEnergy(uSI)
kg m^2 s^-2

julia> getuEnergy(uCGS)
g cm^2 s^-2
```
