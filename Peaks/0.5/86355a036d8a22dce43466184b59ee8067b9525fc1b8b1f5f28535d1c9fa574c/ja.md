```
peakwidths(indices, x, proms; [strict=true, relheight=0.5, min, max]) -> (indices, widths, ledge, redge)
peakwidths(pks::NamedTuple; [strict=true, relheight=0.5, min, max]) -> NamedTuple
```

`proms`と`relheight`に基づいて、`x`内のピーク`indices`の幅を計算し、`min`未満および/または`max`を超える幅のピークを除去します。ピーク、幅、および参照レベルでの左端と右端を返します。

ピーク幅は、ピークの前後で信号が参照レベルを越える距離です。信号の交差はインデックス間で線形補間されます。参照レベルは、ピークの高さと`relheight`の積にピークの顕著性を引いたものです。`NaN`または`missing`の顕著性に対しては幅を計算できません。

NamedTuple `pks`が与えられた場合、`pks`からフィルタリングされたフィールドのコピーを持つ新しいNamedTupleが返されます。`pks`は`:indices`、`:heights`、および`:proms`フィールドを持っている必要があります。`pks`に`:widths`および`:edges`フィールドがある場合、それらは再計算されず、フィルタリングのみが行われます。残りのフィールドは変更されずにコピーされます。

`strict == true`の場合、参照レベルで信号にギャップ（例：`NaN`、`missing`）があるピークの幅はギャップに一致します（例：`NaN`は`NaN`に、など）。そうでない場合、信号の交差はギャップの端の間で線形補間されます。

参照： [`peakwidths!`](@ref), [`peakproms`](@ref), [`findmaxima`](@ref)

# 例

```jldoctest
julia> x = Float64[0,5,2,2,3,3,1,4,0];

julia> pks = findmaxima(x) |> peakproms!(;max=2);

julia> peakwidths(pks)
(indices = [5], heights = [3.0], data = [0.0, 5.0, 2.0, 2.0, 3.0, 3.0, 1.0, 4.0, 0.0], proms = [1.0], widths = [1.75], edges = [(4.5, 6.25)])

julia> x[4] = NaN;

julia> peakwidths(pks.indices, x, pks.proms)
([5], [NaN], [NaN], [6.25])

julia> peakwidths(pks.indices, x, pks.proms; strict=false)
([5], [2.25], [4.0], [6.25])
```
