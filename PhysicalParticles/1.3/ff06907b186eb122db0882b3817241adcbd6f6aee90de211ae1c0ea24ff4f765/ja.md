```
function getuEnergyUnit(::Nothing)
function getuEnergyUnit(units)
```

`units` または `nothing` から質量単位あたりのエネルギーを抽出します

## 例

```jl
julia> getuEnergyUnit(nothing)

julia> getuEnergyUnit(uAstro)
kpc^2 Gyr^-2

julia> getuEnergyUnit(uSI)
m^2 s^-2

julia> getuEnergyUnit(uCGS)
cm^2 s^-2
```
