```
function getuVel(::Nothing)
function getuVel(units)
```

`units` または `nothing` から速度単位を抽出します

## 例

```jl
julia> getuVel(nothing)

julia> getuVel(uAstro)
kpc Gyr^-1

julia> getuVel(uSI)
m s^-1

julia> getuVel(uCGS)
cm s^-1
```
