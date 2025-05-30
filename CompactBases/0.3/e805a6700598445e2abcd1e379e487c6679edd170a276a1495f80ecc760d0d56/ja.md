```
nonempty_intervals(t)
```

ノットセット`t`のすべての非空区間のインデックスを返します。

# 例

```jldoctest
julia> nonempty_intervals(ArbitraryKnotSet(3, [0.0, 1, 1, 3, 4, 6], 1, 3))
4-element Array{Int64,1}:
 1
 3
 4
 5
```
