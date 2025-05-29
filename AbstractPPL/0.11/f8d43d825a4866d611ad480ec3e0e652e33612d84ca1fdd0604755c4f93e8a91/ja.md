```
getsym(vn::VarName)
```

`vn`を生成するために使用されたJulia変数のシンボルを返します。

## 例

```jldoctest
julia> getsym(@varname(x[1][2:3]))
:x

julia> getsym(@varname(y))
:y
```
