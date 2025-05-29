```
latest_value(
    ts::SortedDataFrame,
    at_times::Vector{<:Real};
    assets::Vector{Symbol} = get_assets(ts),
)
```

各入力時刻で最新の価格を取得します。

### 入力

  * `ts` - ティックデータ。
  * `at_times` - 最新の価格を取得したい時刻。
  * `assets` - 最新の価格を取得したい資産。

### 返り値

  * `DataFrame`。行は `at_times` で指定された各時刻に対応します。列は各資産に対応します。
