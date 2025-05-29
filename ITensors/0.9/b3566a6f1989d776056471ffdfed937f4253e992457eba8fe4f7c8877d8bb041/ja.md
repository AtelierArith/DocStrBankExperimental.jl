```
replacetags(i::Index, tsold, tsnew)

replacetags(i::Index, tsold => tsnew)
```

`i`のタグセットが`tsold`で指定されたタグを含む場合、これらを`tsnew`で指定されたタグに置き換え、他のタグは保持します。引数`tsold`と`tsnew`は、カンマ区切りのタグの文字列またはTagSetオブジェクトであることができます。

# 例

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2; tags="l,x", plev=1)
(dim=2|id=83|"l,x")'

julia> replacetags(i, "l", "m")
(dim=2|id=83|"m,x")'

julia> replacetags(i, "l" => "m")
(dim=2|id=83|"m,x")'
```
