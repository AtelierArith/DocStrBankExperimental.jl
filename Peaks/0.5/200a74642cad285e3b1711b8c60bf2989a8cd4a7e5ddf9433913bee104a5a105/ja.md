```
peakheights(indices, heights; [min, max]) -> (indices, heights)
peakheights(pks::NamedTuple; [min, max]) -> NamedTuple
```

`min` より小さいか、または `max` より大きい場合、ピークが削除された `indices` と `heights` のコピーを返します。

NamedTuple `pks` が与えられた場合、`pks` からフィルタリングされたフィールドのコピーを持つ新しい NamedTuple が返されます。`pks` には `:indices` と `:heights` フィールドが必要です。`:proms`、`:widths`、および `:edges` フィールドは存在する場合にフィルタリングされ、残りのフィールドは変更されずにコピーされます。

参照: [`peakproms`](@ref), [`peakwidths`](@ref), [`findmaxima`](@ref)

# 例

```jldoctest
julia> x = [0,5,2,3,3,1,4,0];

julia> pks = findmaxima(x)
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> peakheights(pks; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> inds, heights = peakheights(pks.indices, pks.heights; max=4)
([4, 7], [3, 4])
```
