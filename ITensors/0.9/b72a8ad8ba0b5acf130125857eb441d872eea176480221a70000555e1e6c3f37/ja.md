```
hasid(i::Index, id::ITensors.IDType)
```

指定された id を持つ `Index` `i` があるかどうかを確認します。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2)
(dim=2|id=321)

julia> hasid(i, id(i))
true

julia> j = Index(2)
(dim=2|id=17)

julia> hasid(i, id(j))
false
```
