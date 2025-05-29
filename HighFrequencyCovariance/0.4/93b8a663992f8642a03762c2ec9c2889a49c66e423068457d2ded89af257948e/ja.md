```
DataFrames.combine(
    dfs::Vector{SortedDataFrame{<:Integer}};
    timevar::Symbol = dfs[1].time,
    groupingvar::Symbol = dfs[1].grouping,
    valuevar::Symbol = dfs[1].value,
    period::Dates.Period = dfs[1].time_period_per_unit,
)
```

データフレームのベクトルを結合する

### 入力

  * `dfs` - SortedDataFramesのベクトル
  * `timevar` - 時間を表す列の望ましい名前。
  * `groupingvar` - 資産名を表す列の望ましい名前。
  * `valuevar` - 価格/対数価格/etc.を表す列の望ましい名前。
  * `period` - 時間列の1単位に対応する望ましい期間。
