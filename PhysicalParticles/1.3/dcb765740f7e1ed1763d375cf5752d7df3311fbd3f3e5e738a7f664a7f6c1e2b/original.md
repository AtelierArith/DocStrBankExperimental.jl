```
function getuTime(::Nothing)
function getuTime(units)
```

Extract time unit from `units` or `nothing`

## Examples

```jl
julia> getuTime(nothing)

julia> getuTime(uAstro)
Gyr

julia> getuTime(uSI)
s

julia> getuTime(uCGS)
s
```
