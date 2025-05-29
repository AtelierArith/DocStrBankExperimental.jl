```
filterpeaks!(pks::NT, feature; [min, max]) where {NT<:NamedTuple} -> pks::NT
filterpeaks!(pks::NT, mask) -> pks::NT
```

標準の `pks` フィールドをフィルタリングし、`pks.$feature` が `min` より小さい場合および/または `max` より大きい場合にピークを削除します。`mask` が指定されている場合、指定されたピーク `i` は `mask[i]` が `false` の場合にフィルタリング（削除）されます。

標準の Peaks.jl フィールドの `pks` は `:indices`, `:proms`, `:heights`, `:widths`, `:edges` です。

# 例

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0])
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> filterpeaks!(pks, :heights; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> pks = findmaxima([0,5,2,3,3,1,4,0]) |> peakproms!();

julia> mask = [pks.heights[i] < 5 &&  pks.proms[i] > 2 for i in eachindex(pks.indices)]
3-element Vector{Bool}:
 0
 0
 1

julia> filterpeaks!(pks, mask)
(indices = [7], heights = [4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[3])
```
