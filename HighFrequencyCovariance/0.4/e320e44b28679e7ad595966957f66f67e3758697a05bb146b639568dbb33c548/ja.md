```
two_scales_volatility(vals::Vector, times::Vector, num_grids::Real)
```

Zhang, Mykland, Ait-Sahalia 2005の二スケール法によるボラティリティを計算します。グリッド間隔の時間はデフォルトで総期間の10分の1です。これがあなたの使用法に合わない場合は、マイクロストラクチャノイズの影響が小さいと予想される間隔を選択してください。

### 入力

  * `vals` - 各瞬間の価格。
  * `times` - `vals`の各要素に対応する時間。
  * `num_grids` - 二スケール推定に使用されるグリッドの数。

### 戻り値

  * 資産の推定ボラティリティのスカラー。
  * 資産の推定マイクロストラクチャノイズ分散のスカラー。

    two*scales*volatility(       ts::SortedDataFrame,       assets::Vector{Symbol} = get*assets(ts);       num*grids::Real = default*num*grids(ts),   )

Zhang, Mykland, Ait-Sahalia 2005の二スケール法によるボラティリティを計算します。グリッド間隔の時間はデフォルトで総期間の10分の1です。これがあなたの使用法に合わない場合は、マイクロストラクチャノイズの影響が小さいと予想される間隔を選択してください。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `num_grids` - 二スケール推定に使用されるグリッドの数。

### 戻り値

  * 各資産の推定ボラティリティを含む `Dict`。
  * 各資産の推定マイクロストラクチャノイズ分散を含む `Dict`。

### 参考文献

Zhang L, Mykland PA, Aït-Sahalia Y (2005). "A Tale of Two Time Scales: Determining Integrated Volatility with Noisy High-Frequency Data." Journal of the American Statistical Association, 100(472), 1394–1411. ISSN 01621459. doi:10.1198/016214505000000169. ```
