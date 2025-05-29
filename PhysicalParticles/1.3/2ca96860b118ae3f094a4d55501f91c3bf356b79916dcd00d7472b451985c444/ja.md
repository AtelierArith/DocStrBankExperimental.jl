```
function getuDensity2D(::Nothing)
function getuDensity2D(units)
```

`units` または `nothing` から 2D 密度単位を抽出します

## 例

```jl
julia> getuDensity2D(nothing)

julia> getuDensity2D(uAstro)
M⊙ kpc^-2

julia> getuDensity2D(uSI)
kg m^-2

julia> getuDensity2D(uCGS)
g cm^-2
```
