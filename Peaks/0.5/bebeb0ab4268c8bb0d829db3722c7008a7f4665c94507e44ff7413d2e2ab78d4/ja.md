```
peakheights!(indices, heights; [min, max]) -> (indices, heights)
peakheights!(pks::NamedTuple; [min, max]) -> NamedTuple
```

`min` より小さいピークや `max` より大きいピークを削除することによって `indices` と `heights` をフィルタ（変更）し、返します。

NamedTuple `pks` が与えられた場合、`pks` から同じフィールド（参照）を持つ新しい NamedTuple が返されます。`pks` には `:indices` と `:heights` フィールドが必要です。フィールド `:proms`、`:widths`、および `:edges` が存在する場合はフィルタ（変更）され、残りのフィールドは変更されずに参照されます。

参照: [`peakproms`](@ref), [`peakwidths`](@ref), [`findmaxima`](@ref) [`filterpeaks!`](@ref)

# 例

```jldoctest
julia> x = [0,5,2,3,3,1,4,0];

julia> pks = findmaxima(x)
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> peakheights!(pks; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> inds, heights = peakheights!(pks.indices, pks.heights; min=3.5)
([7], [4])
```
