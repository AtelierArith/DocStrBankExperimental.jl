```
unprefix(vn::VarName, prefix::VarName)
```

VarNameからプレフィックスを削除します。

```jldoctest
julia> AbstractPPL.unprefix(@varname(y.x), @varname(y))
x

julia> AbstractPPL.unprefix(@varname(y.x.a), @varname(y))
x.a

julia> AbstractPPL.unprefix(@varname(y[1].x), @varname(y[1]))
x

julia> AbstractPPL.unprefix(@varname(y), @varname(n))
ERROR: ArgumentError: プレフィックスnをVarName yから削除できませんでした
[...]
```
