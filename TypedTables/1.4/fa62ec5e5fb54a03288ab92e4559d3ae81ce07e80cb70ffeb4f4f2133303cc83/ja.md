```
getproperties(names::Tuple{Vararg{Symbol}})
```

指定された `names` からオブジェクトのプロパティのセットを抽出し、それらのプロパティだけを持つ新しいオブジェクトを返す関数を返します。

内部的に、`names` は定数伝播の目的で `GetProperties` オブジェクトの型パラメータとして保存されます。返されるオブジェクトの型を制御するために `propertytype` 関数をオーバーロードすることができ、デフォルトでは `NamedTuple` になります。`getproperty` も参照してください。

# 例

`NamedTuple` からプロパティ `a` と `c` を抽出します。

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> getproperties((:a, :c))(nt)
(a = 1, c = false)
```
