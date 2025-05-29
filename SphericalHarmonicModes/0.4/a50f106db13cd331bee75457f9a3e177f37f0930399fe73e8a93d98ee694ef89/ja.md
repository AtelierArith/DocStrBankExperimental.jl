```
L1L2Triangle(l1_min::Int, l1_max::Int, Δl_max::Int, l2_min::Int = max(0, l1_min - Δl_max), l2_max = l1_max + Δl_max)
L1L2Triangle(l1_range::AbstractUnitRange{Int}, Δl_max::Int, l2_range::AbstractUnitRange{Int})
```

`l1_range` にある `l1` のペアと `l2_range` にある `l2` のペアをループするイテレータを返します。ここで、`l2` と `l1` は三角形条件 `max(0, l1 - Δl_max) ⩽ l2 ⩽ l1 + Δl_max` を満たします。`l2_range` が指定されていない場合、許可される最大範囲がデフォルトとなります。

!!! warning
    範囲 `l1_range` と `l2_range` は最小限の許可される部分集合に制限されます。


# 例

```jldoctest
julia> L1L2Triangle(1:2, 2) |> collect
9-element Vector{Tuple{Int64, Int64}}:
 (1, 0)
 (1, 1)
 (1, 2)
 (1, 3)
 (2, 0)
 (2, 1)
 (2, 2)
 (2, 3)
 (2, 4)

julia> L1L2Triangle(2:3, 1) |> collect
6-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (2, 2)
 (2, 3)
 (3, 2)
 (3, 3)
 (3, 4)

julia> L1L2Triangle(2:3, 1, 2:3) |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (2, 3)
 (3, 2)
 (3, 3)
```
