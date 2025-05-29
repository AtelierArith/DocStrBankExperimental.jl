```
function getuDensity(::Nothing)
function getuDensity(units)
```

`units` または `nothing` から 3D 密度単位を抽出します

## 例

```jl
julia> getuDensity(nothing)

julia> getuDensity(uAstro)
M⊙ kpc^-3

julia> getuDensity(uSI)
kg m^-3

julia> getuDensity(uCGS)
g cm^-3
```
