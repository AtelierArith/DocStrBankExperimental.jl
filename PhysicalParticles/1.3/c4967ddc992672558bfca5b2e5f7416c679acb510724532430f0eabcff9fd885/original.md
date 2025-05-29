```
function getuLength(::Nothing)
function getuLength(units)
```

Extract length unit from `units` or `nothing`

## Examples

```jl
julia> getuLength(nothing)

julia> getuLength(uAstro)
kpc

julia> getuLength(uSI)
m

julia> getuLength(uCGS)
cm
```
