```
cost,i1,i2 = dtw(seq1, seq2, [dist=SqEuclidean, postprocess=nothing])
cost,i1,i2 = dtw(seq1, seq2, dist, i2min, i2max)
```

動的時間伸縮を行い、2つの系列間の距離を測定します。

動的軸伸縮によって2つの系列（`seq1`、`seq2`）を整列させるインデックスのセット（`i1`、`i2`）を見つけます。また、距離（伸縮後）を、デフォルトで二乗ユークリッド距離となるSemiMetric `dist`に従って返します（詳細はDistances.jlを参照）。`seq1`と`seq2`が行列の場合、各列は観測値と見なされます。

`i2min/max`が提供されている場合、ウィンドウに制限された`seq1`と`seq2`を整列させるためにDTWを行います。ベクトル`i2min`と`i2max`は、`seq1`の各インデックスに対する`seq2`の（含む）下限および上限を指定します。したがって、`i2min`と`i2max`は`seq1`と同じ長さである必要があります。

`filternernel::AbstractMatrix`が提供されている場合、コスト行列をフィルタリングするために使用されます。例えば、`ImageFiltering.Kernel.gaussian(3)`を使用して適切なカーネルを作成します。コスト行列のフィルタリングは、伸縮を滑らかにし、小規模な伸縮に対して効果的にペナルティを課します。

さらに[`dtw_cost`](@ref)および[`dtwnn`](@ref)も参照してください。
