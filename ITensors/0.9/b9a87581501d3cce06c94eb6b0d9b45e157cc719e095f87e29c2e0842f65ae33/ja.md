```
hasplev(i::Index, plev::Int)
```

指定されたプライムレベルを持つ`Index` `i`を確認します。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2; plev=2)
(dim=2|id=543)''

julia> hasplev(i, 2)
true

julia> hasplev(i, 1)
false
```
