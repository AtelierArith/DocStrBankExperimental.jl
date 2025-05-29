```
deleteproperties(object, names::Tuple{Vararg{Symbol}})
```

与えられた `names` のプロパティを削除した `object` のコピーを返します。

# 例

```
julia> nt = (a = 1, b = 2.0, c = false, d = "abc")
(a = 1, b = 2.0, c = false)

julia> deleteproperties(nt, (:b, :d))
(a = 1, c = false)
```
