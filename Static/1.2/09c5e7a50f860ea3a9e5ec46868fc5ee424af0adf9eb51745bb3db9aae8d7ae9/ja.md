```
NDIndex(i, j, k...)   -> I
NDIndex((i, j, k...)) -> I
```

単一の要素を参照する多次元インデックス。各次元は単一の `Int` または `StaticInt` で表されます。

```julia
julia> using Static

julia> i = NDIndex(static(1), 2, static(3))
NDIndex(static(1), 2, static(3))

julia> i[static(1)]
static(1)

julia> i[1]
1

```
