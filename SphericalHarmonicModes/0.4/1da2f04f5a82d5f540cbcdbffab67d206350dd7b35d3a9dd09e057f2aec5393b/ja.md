```
L2L1Triangle(l1_min::Int, l1_max::Int, Δl_max::Int, l2_min::Int = max(0, l1_min - Δl_max), l2_max = l1_max + Δl_max)
L2L1Triangle(l1_range::AbstractUnitRange{Int}, Δl_max::Int, l2_range::AbstractUnitRange{Int})
```

`(l2,l1)` のペアをループするイテレータを返します。ここで `l1` は `l1_range` にあり、`l2` は `l2_range` にあり、`l2` と `l1` は三角形条件 `max(0, l1 - Δl_max) ⩽ l2 ⩽ l1 + Δl_max` を満たします。`l2_range` が指定されていない場合、許可される最大範囲がデフォルトとなります。

!!! warning
    範囲 `l1_range` と `l2_range` は最小限の許可される部分集合に制限されます。


# 例

```jldoctest
julia> L2L1Triangle(1:2, 2) |> collect
9-element Vector{Tuple{Int64, Int64}}:
 (0, 1)
 (1, 1)
 (2, 1)
 (3, 1)
 (0, 2)
 (1, 2)
 (2, 2)
 (3, 2)
 (4, 2)

julia> L2L1Triangle(2:3, 1) |> collect
6-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (2, 2)
 (3, 2)
 (2, 3)
 (3, 3)
 (4, 3)

julia> L2L1Triangle(2:3, 1, 2:3) |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 2)
 (2, 3)
 (3, 3)
```
