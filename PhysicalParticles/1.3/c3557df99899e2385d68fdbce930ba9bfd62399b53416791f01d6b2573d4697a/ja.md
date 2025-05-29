```
function getuAmount(::Nothing)
function getuAmount(units)
```

`units` または `nothing` から量の単位を抽出します

## 例

```jl
julia> getuAmount(nothing)

julia> getuAmount(uAstro)
mol

julia> getuAmount(uSI)
mol

julia> getuAmount(uCGS)
mol
```
