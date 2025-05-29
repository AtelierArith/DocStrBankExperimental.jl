```
function getuLuminosity(::Nothing)
function getuLuminosity(units)
```

`units` または `nothing` から光度単位を抽出します

## 例

```jl
julia> getuLuminosity(nothing)

julia> getuLuminosity(uAstro)
cd

julia> getuLuminosity(uSI)
cd

julia> getuLuminosity(uCGS)
cd
```
