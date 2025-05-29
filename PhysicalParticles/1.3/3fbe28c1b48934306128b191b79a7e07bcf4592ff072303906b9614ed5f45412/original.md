```
function getuMass(::Nothing)
function getuMass(units)
```

Extract mass unit from `units` or `nothing`

## Examples

```jl
julia> getuMass(nothing)

julia> getuMass(uAstro)
M⊙

julia> getuMass(uSI)
kg

julia> getuMass(uCGS)
g
```
