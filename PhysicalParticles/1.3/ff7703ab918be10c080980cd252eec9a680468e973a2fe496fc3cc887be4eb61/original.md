```
function getuTemperature(::Nothing)
function getuTemperature(units)
```

Extract temperature unit from `units` or `nothing`

## Examples

```jl
julia> getuTemperature(nothing)

julia> getuTemperature(uAstro)
K

julia> getuTemperature(uSI)
K

julia> getuTemperature(uCGS)
K
```
