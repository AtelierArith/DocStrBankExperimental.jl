```
VarName(vn::VarName, optic)
VarName(vn::VarName, indexing::Tuple)

`vn`の新しいインデックス`optic`/`indexing`を持つコピーを返します。

```

jldoctest; setup=:(using Accessors) julia> VarName(@varname(x[1][2:3]), Accessors.IndexLens((2,))) x[2]

julia> VarName(@varname(x[1][2:3]), ((2,),)) x[2]

julia> VarName(@varname(x[1][2:3])) x

```

```
