```
function getuLength(::Nothing)
function getuLength(units)
```

`units` または `nothing` から長さの単位を抽出します

## 例

```jl
julia> getuLength(nothing)

julia> getuLength(uAstro)
kpc

julia> getuLength(uSI)
m

julia> getuLength(uCGS)
cm
```
