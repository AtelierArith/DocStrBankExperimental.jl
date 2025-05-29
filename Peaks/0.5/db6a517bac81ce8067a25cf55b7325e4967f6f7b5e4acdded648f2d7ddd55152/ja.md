```
peakwidths!(indices, x; [strict=true, relheight=0.5, min, max]) -> (indices, widths, ledge, redge)
peakwidths!(pks::NamedTuple; [strict=true, relheight=0.5, min, max]) -> NamedTuple
```

`x`におけるピーク`indices`の幅を、`proms`と`relheight`に基づく基準レベルで計算し、`min`未満および/または`max`を超える幅のピークを除去します。修正されたピーク、幅、および基準レベルでの左端と右端を返します。

NamedTuple `pks`が与えられた場合、`pks`から同じフィールド（参照）を持つ新しいNamedTupleが返されます。`pks`は`:indices`、`:heights`、および`:proms`フィールドを持っている必要があります。`pks`に`:widths`および`:edges`フィールドがある場合、それらは再計算されず、フィルタリングのみが行われます。残りのフィールドは変更されずにコピーされます。

参照: [`peakwidths`](@ref), [`peakproms`](@ref), [`findmaxima`](@ref)

# 

# 例

```jldoctest ; filter = r"(\d*)\.(\d{3})\d*" => s"\1.\2***"
julia> x = Float64[0,5,2,2,3,3,1,4,0];

julia> pks = findmaxima(x) |> peakproms!();

julia> peakwidths!(pks; min=1)
(indices = [2, 5], heights = [5.0, 3.0], data = [0.0, 5.0, 2.0, 2.0, 3.0, 3.0, 1.0, 4.0, 0.0], proms = [5.0, 1.0], widths = [1.333, 1.75], edges = [(1.5, 2.833), (4.5, 6.25)])

julia> peakwidths!(pks.indices, pks.data, pks.proms; min=1)
([2, 5], [1.333, 1.75], [1.5, 4.5], [2.833, 6.25])
```
