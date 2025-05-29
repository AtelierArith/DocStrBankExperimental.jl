```
prefix(vn::VarName, prefix::VarName)
```

VarNameにプレフィックスを追加します。

```jldoctest
julia> AbstractPPL.prefix(@varname(x), @varname(y))
y.x

julia> AbstractPPL.prefix(@varname(x.a), @varname(y))
y.x.a

julia> AbstractPPL.prefix(@varname(x.a), @varname(y[1]))
y[1].x.a
```
