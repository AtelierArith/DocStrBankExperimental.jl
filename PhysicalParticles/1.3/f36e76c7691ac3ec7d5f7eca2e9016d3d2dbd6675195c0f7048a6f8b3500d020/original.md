```
function getuVel(::Nothing)
function getuVel(units)
```

Extract velocity unit from `units` or `nothing`

## Examples

```jl
julia> getuVel(nothing)

julia> getuVel(uAstro)
kpc Gyr^-1

julia> getuVel(uSI)
m s^-1

julia> getuVel(uCGS)
cm s^-1
```
