```
function getuMomentumAngular(::Nothing)
function getuMomentumAngular(units)
```

Extract momentum unit from `units` or `nothing`

## Examples

```jl
julia> getuMomentumAngular(nothing)

julia> getuMomentumAngular(uAstro)
kpc^2 M⊙ Gyr^-1

julia> getuMomentumAngular(uSI)
kg m^2 s^-1

julia> getuMomentumAngular(uCGS)
g cm^2 s^-1
```
