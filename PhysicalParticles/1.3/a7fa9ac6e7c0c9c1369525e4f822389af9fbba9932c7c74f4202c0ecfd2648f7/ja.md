```
function getuAcc(::Nothing)
function getuAcc(units)
```

`units` または `nothing` から加速度単位を抽出します

## 例

```jl
julia> getuAcc(nothing)

julia> getuAcc(uAstro)
kpc Gyr^-2

julia> getuAcc(uSI)
m s^-2

julia> getuAcc(uCGS)
cm s^-2
```
