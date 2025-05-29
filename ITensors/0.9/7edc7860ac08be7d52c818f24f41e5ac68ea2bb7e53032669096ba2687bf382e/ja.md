```
Index(dim::Int; tags::Union{AbstractString, TagSet} = "",
                plev::Int = 0)
```

ユニークな `id`、`tags` で与えられた TagSet、および素数レベル `plev` を持つ `Index` を作成します。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2; tags="l", plev=1)
(dim=2|id=818|"l")'

julia> dim(i)
2

julia> plev(i)
1

julia> tags(i)
"l"
```
