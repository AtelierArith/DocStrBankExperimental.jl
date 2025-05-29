```
estimate_microstructure_noise(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    num_grids::Real = default_num_grids(ts),
)
```

これは二重スケールボラティリティ法を用いてマイクロストラクチャノイズを推定します。

### 入力

  * `ts` - ティックデータ。
  * `assets` - tsから共分散を推定したい資産。
  * `num_grids` - 二重スケール推定に使用されるグリッドの数。

### 返り値

  * 各資産の推定されたマイクロストラクチャノイズ分散を含む`Dict`。
