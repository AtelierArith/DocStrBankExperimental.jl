```
function getuCurrent(::Nothing)
function getuCurrent(units)
```

Extract electric current unit from `units` or `nothing`

## Examples

```jl
julia> getuCurrent(nothing)

julia> getuCurrent(uAstro)
A

julia> getuCurrent(uSI)
A

julia> getuCurrent(uCGS)
A
```
