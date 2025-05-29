```
LazyRow(s::StructArray, i)
```

`s[i]`の遅延表現。`LazyRow(s, i)`は`i`番目の行を具現化せず、それに対する遅延ラッパーを返し、`getproperty`が正しく動作します。これは、行に多くのフィールドがあり、そのうちのいくつかだけが必要な場合に便利です。また、列をその場で変更することも可能です。

`LazyRow`のイテレータを取得するには、[`LazyRows`](@ref)を参照してください。

# 例

```julia-repl
julia> t = StructArray((a = [1, 2], b = ["x", "y"]));

julia> LazyRow(t, 2).a
2

julia> LazyRow(t, 2).a = 123
123

julia> t
2-element StructArray(::Array{Int64,1}, ::Array{String,1}) with eltype NamedTuple{(:a, :b),Tuple{Int64,String}}:
 (a = 1, b = "x")
 (a = 123, b = "y")
```
