```
schema(::Type)
```

`schema` は型を扱いやすい値に変換します。

例:

```
julia> nt = (a=(b=[1,2],c=(d=[3,4],e=[5,6])),f=[7,8]);

julia> NT = typeof(nt)
NamedTuple{(:a, :f),Tuple{NamedTuple{(:b, :c),Tuple{Array{Int64,1},NamedTuple{(:d, :e),Tuple{Array{Int64,1},Array{Int64,1}}}}},Array{Int64,1}}}

julia> schema(NT)
(a = (b = Array{Int64,1}, c = (d = Array{Int64,1}, e = Array{Int64,1})), f = Array{Int64,1})
```
