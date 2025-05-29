```
peakproms(indices, x; [strict=true, min, max]) -> (indices, proms)
peakproms(pks::NamedTuple; [strict=true, min, max]) -> NamedTuple
```

`x`のピーク`indices`のプロミネンスを計算し、`min`未満または`max`を超えるプロミネンスを持つピークを削除します。

ピークのプロミネンスは、現在のピークと、現在のピークと隣接する大きなピークまたは信号の端の間にある2つの隣接する最小マグニチュードポイントのうちの大きい方との絶対的な高さ（値）の差です。

NamedTuple `pks`が与えられた場合、`pks`からフィルタリングされたフィールドのコピーを持つ新しいNamedTupleが返されます。`pks`には`:indices`および`:heights`フィールドが必要です。`pks`に`:proms`フィールドがある場合、プロミネンスはフィルタリングされるだけで再計算されません。`:widths`および`:edges`フィールドも存在する場合はフィルタリングされ、残りのフィールドは変更されずにコピーされます。

`strict == true`の場合、現在のピークと隣接する大きなピークの間に`NaN`または`missing`があるピークのプロミネンスは`NaN`または`missing`になります。そうでない場合、`strict == false`のときは、現在のピークと隣接する大きなピークの間の最小の非`NaN`または`missing`値の大きい方になります。

参照: [`peakproms!`](@ref), [`findmaxima`](@ref)

# 例

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0]);

julia> pks = peakproms(pks; min=2)
(indices = [2, 7], heights = [5, 4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[5, 3])

julia> inds, proms = peakproms(pks.indices, pks.data; max=4)
([7], Union{Missing, Int64}[3])
```
