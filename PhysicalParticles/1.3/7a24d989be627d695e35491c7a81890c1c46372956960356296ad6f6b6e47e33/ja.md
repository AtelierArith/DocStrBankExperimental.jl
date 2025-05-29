```
function getuMomentumAngular(::Nothing)
function getuMomentumAngular(units)
```

`units` または `nothing` から運動量単位を抽出します

## 例

```jl
julia> getuMomentumAngular(nothing)

julia> getuMomentumAngular(uAstro)
kpc^2 M⊙ Gyr^-1

julia> getuMomentumAngular(uSI)
kg m^2 s^-1

julia> getuMomentumAngular(uCGS)
g cm^2 s^-1
```
