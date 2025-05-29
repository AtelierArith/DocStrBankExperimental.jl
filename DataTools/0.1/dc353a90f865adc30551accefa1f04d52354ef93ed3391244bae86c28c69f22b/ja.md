```
firstitem(xs)
```

`xs`の最初のアイテムを取得します。必要に応じて`xs`を消費します。

# 例

```jldoctest
julia> using DataTools, Transducers

julia> firstitem(3:7)
3

julia> 3:7 |> Map(x -> x + 1) |> Filter(isodd) |> firstitem
5
```
