```
unprefix(vn::VarName, prefix::VarName)
```

Remove a prefix from a VarName.

```jldoctest
julia> AbstractPPL.unprefix(@varname(y.x), @varname(y))
x

julia> AbstractPPL.unprefix(@varname(y.x.a), @varname(y))
x.a

julia> AbstractPPL.unprefix(@varname(y[1].x), @varname(y[1]))
x

julia> AbstractPPL.unprefix(@varname(y), @varname(n))
ERROR: ArgumentError: could not remove prefix n from VarName y
[...]
```
