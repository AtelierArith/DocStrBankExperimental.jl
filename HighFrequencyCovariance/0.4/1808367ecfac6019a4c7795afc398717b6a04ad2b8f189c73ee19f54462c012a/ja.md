```
time_between_refreshes(
   ts::SortedDataFrame;
   assets::Vector{Symbol} = get_assets(ts),
)
```

各リフレッシュ間の時間と合計ティック数を示す `DataFrame` を取得します。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ラベルの `Vector`。

### 返り値

  * 各資産のティック間の平均時間を要約した `DataFrame`。
