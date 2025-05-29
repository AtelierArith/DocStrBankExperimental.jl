```
anchorrange(anchor; step, start, stop, pre, post)
```

`anchor`をグリッド上におおよそ持つ範囲を返します。

```jldoctest
julia> using RangeHelpers

julia> anchorrange(15.5, start=above(11), step=2, stop=below(15))
11.5:2.0:13.5
```
