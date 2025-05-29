```
scatter(snd;source=MAIN)
```

コレクション `snd[source]` のアイテムを、`snd` と同じサイズおよびコンテナタイプの配列にコピーします。この関数は `length(snd[source]) == length(snd)` を必要とします。

# 例

```jldoctest
julia> using PartitionedArrays

julia> a = [Int[],[1,2,3],Int[]]
3-element Vector{Vector{Int64}}:
 []
 [1, 2, 3]
 []

julia> scatter(a,source=2)
3-element Vector{Int64}:
 1
 2
 3
```
