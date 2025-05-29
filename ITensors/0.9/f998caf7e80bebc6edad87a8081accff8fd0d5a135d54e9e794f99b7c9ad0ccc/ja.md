```
Index(dim::Integer, tags::Union{AbstractString, TagSet}; plev::Int = 0)
```

ユニークな `id` と `tags` によって与えられたタグセットを持つ `Index` を作成します。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2, "l,tag")
(dim=2|id=58|"l,tag")

julia> dim(i)
2

julia> plev(i)
0

julia> tags(i)
"l,tag"
```
