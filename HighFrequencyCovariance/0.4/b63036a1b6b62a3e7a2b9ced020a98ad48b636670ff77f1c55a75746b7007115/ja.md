```
ticks_per_asset(ts::SortedDataFrame, assets::Vector{Symbol} = get_assets(ts))
```

各資産の観測数をカウントします。

### 入力

  * `ts` - ティックデータ
  * `assets` - 資産の`Symbol`を含むベクター。

### 返り値

  * 各入力資産の観測数を含む`Dict`。
