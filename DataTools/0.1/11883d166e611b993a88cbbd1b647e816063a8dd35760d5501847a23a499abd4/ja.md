```
lastitem(xs)
```

`xs`の最後のアイテムを取得します。必要に応じて`xs`を消費します。

# 例

```jldoctest
julia> using DataTools, Transducers

julia> lastitem(3:7)
7

julia> 3:7 |> Map(x -> x + 1) |> Filter(isodd) |> lastitem
7
```
