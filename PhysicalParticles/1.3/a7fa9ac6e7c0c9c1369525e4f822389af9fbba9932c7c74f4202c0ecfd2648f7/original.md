```
function getuAcc(::Nothing)
function getuAcc(units)
```

Extract acceleration unit from `units` or `nothing`

## Examples

```jl
julia> getuAcc(nothing)

julia> getuAcc(uAstro)
kpc Gyr^-2

julia> getuAcc(uSI)
m s^-2

julia> getuAcc(uCGS)
cm s^-2
```
