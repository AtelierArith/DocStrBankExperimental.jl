```
function getuLuminosity(::Nothing)
function getuLuminosity(units)
```

Extract luminosity unit from `units` or `nothing`

## Examples

```jl
julia> getuLuminosity(nothing)

julia> getuLuminosity(uAstro)
cd

julia> getuLuminosity(uSI)
cd

julia> getuLuminosity(uCGS)
cd
```
