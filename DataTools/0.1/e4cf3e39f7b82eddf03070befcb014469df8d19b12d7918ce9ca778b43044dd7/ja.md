```
nitems(xs) -> n::Integer
```

`xs`のアイテム数をカウントします。必要に応じて`xs`を消費します。

# 例

```jldoctest
julia> using DataTools, Transducers

julia> nitems(1:10)
10

julia> 1:10 |> Filter(isodd) |> Map(inv) |> nitems
5
```
