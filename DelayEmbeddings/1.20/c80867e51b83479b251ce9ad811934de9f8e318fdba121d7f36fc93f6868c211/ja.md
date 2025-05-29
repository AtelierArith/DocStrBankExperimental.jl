```
mdop_maximum_delay(s, tw = 1:50, samplesize = 1.0)) -> τ_max, L
```

最適遅延の探索の上限を計算します。これは、`mdop_embedding` [`mdop_embedding`](@ref) または `beta_statistic` [`beta_statistic`](@ref) を使用する際に適用されます。

## 説明

入力時系列 `s` は、単位ラグと次第に増加する次元で埋め込まれます。次元（または時間ウィンドウ） `tw` （`RangeObject`）ごとに、Uzal et al. の `L`-統計量 [^Uzal2011] が計算されます。`samplesize` は、`L` の計算に考慮されるポイントの割合を決定します（[`uzal_cost`](@ref) を参照）。この統計量がグローバル最小値に達すると、最大遅延値 `τ_max` が返されます。`s` が多変量 `Dataset` の場合、`τ_max` はそのデータセットのすべての時系列について計算され、最大値が返されます。返される `L`-統計量のサイズは `(length(tw), size(s,2))` です。

[^Nichkawde2013]: Nichkawde, Chetan (2013). [Optimal state-space reconstruction using derivatives on projected manifold. Physical Review E 87, 022905](https://doi.org/10.1103/PhysRevE.87.022905).

[^Uzal2011]: Uzal, L. C., Grinblat, G. L., Verdes, P. F. (2011). [Optimal reconstruction of dynamical systems: A noise amplification approach. Physical Review E 84, 016223](https://doi.org/10.1103/PhysRevE.84.016223).
