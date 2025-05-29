```
function getuTime(::Nothing)
function getuTime(units)
```

`units` または `nothing` から時間単位を抽出します

## 例

```jl
julia> getuTime(nothing)

julia> getuTime(uAstro)
Gyr

julia> getuTime(uSI)
s

julia> getuTime(uCGS)
s
```
