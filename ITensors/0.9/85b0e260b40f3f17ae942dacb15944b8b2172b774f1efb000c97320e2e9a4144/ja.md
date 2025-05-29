```
settags(i::Index, ts)
```

Index `i` のタグを指定されたタグに置き換えたコピーを返します。`ts` 引数は、カンマ区切りのタグの文字列または TagSet であることができます。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2, "SpinHalf,Site,n=3")
(dim=2|id=543|"Site,SpinHalf,n=3")

julia> hastags(i, "Link")
false

julia> j = settags(i, "Link,n=4")
(dim=2|id=543|"Link,n=4")

julia> hastags(j, "Link")
true

julia> hastags(j, "n=4,Link")
true
```
