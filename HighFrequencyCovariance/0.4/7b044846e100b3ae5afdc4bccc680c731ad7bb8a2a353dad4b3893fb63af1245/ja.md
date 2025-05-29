```
random_value_in_interval(
   ts::SortedDataFrame,
   at_times::Vector{<:Real};
   assets::Vector{Symbol} = get_assets(ts),
   twister_arb_value_in_interval::MersenneTwister = MersenneTwister(2604),
)
```

区間内のランダムな値を取得します。したがって、1、7、8の時刻を入力すると、2番目のエントリでは、時刻1と7の間のランダムな更新（存在する場合）を選択します。

### 入力

  * `ts` - ティックデータ。
  * `at_times` - 興味のある区間を分ける時刻。
  * `assets` - 興味のある資産。
  * `twister_arb_value_in_interval` - ランダムな区間を選択するために使用されるRNG。

### 戻り値

  * 各区間のランダムなティックからの各資産の価格を含む`DataFrame`。
