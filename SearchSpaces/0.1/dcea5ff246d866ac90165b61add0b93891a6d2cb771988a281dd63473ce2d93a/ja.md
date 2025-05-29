```
BoxConstrainedSpace(;lb, ub, rigid=true)
```

ボックス制約によって区切られた探索空間を定義します。

# 例

```julia-repl
julia> space = BoxConstrainedSpace(lb = zeros(Int, 5), ub = ones(Int, 5))
BoxConstrainedSpace{Int64}([0, 0, 0, 0, 0], [1, 1, 1, 1, 1], [1, 1, 1, 1, 1], 5, true)

julia> cardinality(space)
32
```
