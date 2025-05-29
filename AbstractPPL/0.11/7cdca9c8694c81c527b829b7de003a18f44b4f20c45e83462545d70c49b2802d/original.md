```
VarName(vn::VarName, optic)
VarName(vn::VarName, indexing::Tuple)
```

Return a copy of `vn` with a new index `optic`/`indexing`.

```jldoctest; setup=:(using Accessors)
julia> VarName(@varname(x[1][2:3]), Accessors.IndexLens((2,)))
x[2]

julia> VarName(@varname(x[1][2:3]), ((2,),))
x[2]

julia> VarName(@varname(x[1][2:3]))
x
```
