```
function getuTemperature(::Nothing)
function getuTemperature(units)
```

`units` または `nothing` から温度単位を抽出します

## 例

```jl
julia> getuTemperature(nothing)

julia> getuTemperature(uAstro)
K

julia> getuTemperature(uSI)
K

julia> getuTemperature(uCGS)
K
```
