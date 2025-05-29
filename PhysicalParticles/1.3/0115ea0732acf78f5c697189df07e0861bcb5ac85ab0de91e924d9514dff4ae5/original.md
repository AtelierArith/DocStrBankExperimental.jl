```
function getuMomentum(::Nothing)
function getuMomentum(units)
```

Extract momentum unit from `units` or `nothing`

## Examples

```jl
julia> getuMomentum(nothing)

julia> getuMomentum(uAstro)
kpc M⊙ Gyr^-1

julia> getuMomentum(uSI)
kg m s^-1

julia> getuMomentum(uCGS)
g cm s^-1
```
