```
function getuEntropy(::Nothing)
function getuEntropy(units)
```

Extract entropy unit from `units` or `nothing`

## Examples

```jl
julia> getuEntropy(nothing)

julia> getuEntropy(uAstro)
kpc^2 M⊙ K^-1 Gyr^-2

julia> getuEntropy(uSI)
kg m^2 K^-1 s^-2

julia> getuEntropy(uCGS)
g cm^2 K^-1 s^-2
```
