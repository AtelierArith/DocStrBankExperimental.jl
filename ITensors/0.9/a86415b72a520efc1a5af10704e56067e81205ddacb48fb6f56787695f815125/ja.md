```
hastags(i::Index, ts::Union{AbstractString,TagSet})
```

`Index` `i` が提供されたタグを持っているか確認します。タグはカンマ区切りの文字列または TagSet オブジェクトであることができます。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2, "SpinHalf,Site,n=3")
(dim=2|id=861|"Site,SpinHalf,n=3")

julia> hastags(i, "SpinHalf,Site")
true

julia> hastags(i, "Link")
false
```
