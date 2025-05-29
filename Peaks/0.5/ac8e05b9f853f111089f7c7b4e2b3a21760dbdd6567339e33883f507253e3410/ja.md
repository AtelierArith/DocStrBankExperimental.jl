```
peakproms!(indices, x; [strict=true, min, max]) -> (indices, proms)
peakproms!(pks::NamedTuple; [strict=true, min, max]) -> NamedTuple
```

配列 `x` におけるピーク `indices` のプロミネンスを計算し、`min` より小さいおよび/または `max` より大きいプロミネンスを持つピークを削除します。

NamedTuple `pks` が与えられた場合、`pks` から同じフィールド（参照）を持つ新しい NamedTuple が返されます。`pks` には `:indices` と `:heights` フィールドが必要です。`pks` に `:proms` フィールドがある場合、プロミネンスはフィルタリングされるだけで再計算されません。`:widths` および `:edges` フィールドも存在する場合はフィルタリング（変更）され、残りのフィールドは変更されずにコピーされます。

関連情報: [`peakproms`](@ref), [`findmaxima`](@ref)

# 

# 例

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0]);

julia> pks = peakproms!(pks; min=2)
(indices = [2, 7], heights = [5, 4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[5, 3])

julia> inds, proms = peakproms!(pks.indices, pks.data; max=4)
([7], Union{Missing, Int64}[3])
```
