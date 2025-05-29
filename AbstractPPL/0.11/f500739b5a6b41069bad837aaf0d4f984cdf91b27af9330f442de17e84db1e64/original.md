```
getoptic(vn::VarName)
```

Return the optic of the Julia variable used to generate `vn`.

## Examples

```jldoctest
julia> getoptic(@varname(x[1][2:3]))
(@o _[1][2:3])

julia> getoptic(@varname(y))
identity (generic function with 1 method)
```
