```
function getuEnergy(::Nothing)
function getuEnergy(units)
```

`units` または `nothing` からエネルギー単位を抽出します

## 例

```jl
julia> getuEnergy(nothing)

julia> getuEnergy(uAstro)
kpc^2 M⊙ Gyr^-2

julia> getuEnergy(uSI)
kg m^2 s^-2

julia> getuEnergy(uCGS)
g cm^2 s^-2
```
