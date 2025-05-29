```
getproperties(object, names::Tuple{Vararg{Symbol}})
```

指定された `names` から `object` から一連のプロパティを抽出し、それらのプロパティだけを持つ新しいオブジェクトを返します。

# 例

`NamedTuple` からプロパティ `a` と `c` を抽出します。

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> getproperties(nt, (:a, :c))
(a = 1, c = false)
```
