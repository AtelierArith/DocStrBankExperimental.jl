```
function getuAmount(::Nothing)
function getuAmount(units)
```

Extract amount unit from `units` or `nothing`

## Examples

```jl
julia> getuAmount(nothing)

julia> getuAmount(uAstro)
mol

julia> getuAmount(uSI)
mol

julia> getuAmount(uCGS)
mol
```
