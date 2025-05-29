```
function getuMass(::Nothing)
function getuMass(units)
```

`units` または `nothing` から質量単位を抽出します

## 例

```jl
julia> getuMass(nothing)

julia> getuMass(uAstro)
M⊙

julia> getuMass(uSI)
kg

julia> getuMass(uCGS)
g
```
