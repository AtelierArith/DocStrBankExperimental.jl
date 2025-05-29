```
prefix(vn::VarName, prefix::VarName)
```

Add a prefix to a VarName.

```jldoctest
julia> AbstractPPL.prefix(@varname(x), @varname(y))
y.x

julia> AbstractPPL.prefix(@varname(x.a), @varname(y))
y.x.a

julia> AbstractPPL.prefix(@varname(x.a), @varname(y[1]))
y[1].x.a
```
