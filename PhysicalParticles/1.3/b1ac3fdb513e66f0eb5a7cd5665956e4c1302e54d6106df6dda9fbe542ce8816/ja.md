```
function getuCurrent(::Nothing)
function getuCurrent(units)
```

`units` または `nothing` から電流単位を抽出します

## 例

```jl
julia> getuCurrent(nothing)

julia> getuCurrent(uAstro)
A

julia> getuCurrent(uSI)
A

julia> getuCurrent(uCGS)
A
```
