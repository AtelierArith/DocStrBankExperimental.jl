```
function getuMomentum(::Nothing)
function getuMomentum(units)
```

`units` または `nothing` から運動量の単位を抽出します

## 例

```jl
julia> getuMomentum(nothing)

julia> getuMomentum(uAstro)
kpc M⊙ Gyr^-1

julia> getuMomentum(uSI)
kg m s^-1

julia> getuMomentum(uCGS)
g cm s^-1
```
