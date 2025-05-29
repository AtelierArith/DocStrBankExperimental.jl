```
function getuPressure(::Nothing)
function getuPressure(units)
```

`units` または `nothing` から 2D 密度単位を抽出します

## 例

```jl
julia> getuPressure(nothing)

julia> getuPressure(uAstro)
M⊙ kpc^-1 Gyr^-2

julia> getuPressure(uSI)
kg m^-1 s^-2

julia> getuPressure(uCGS)
g cm^-1 s^-2
```
