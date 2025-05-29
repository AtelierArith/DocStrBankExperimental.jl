```
get_all_refresh_times(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    start_time::R = minimum(ts.df[:, ts.time]),
) where R<:Real
```

すべての資産が更新された価格を持つときのすべてのリフレッシュ時間のベクトルを取得します。したがって、資産AとBがそれぞれ(1,5,6,7,10)および(2,5,7,9)で取引されている場合、リフレッシュ時間は(2,5,7,10)になります。これらの4つの時間では、前回のリフレッシュ時間以降にすべての資産の更新された価格があります。

### 入力

  * `ts` - ティックデータ。
  * `assets` - 興味のある資産。
  * `start_time` - 更新された価格を探し始める時間。

### 戻り値

  * リフレッシュ時間の`Vector`。
