```
getoptic(vn::VarName)
```

`vn`を生成するために使用されたJulia変数のオプティックを返します。

## 例

```jldoctest
julia> getoptic(@varname(x[1][2:3]))
(@o _[1][2:3])

julia> getoptic(@varname(y))
identity (generic function with 1 method)
```
