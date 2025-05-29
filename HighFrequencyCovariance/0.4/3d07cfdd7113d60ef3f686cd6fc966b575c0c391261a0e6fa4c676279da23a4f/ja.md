```
duration(ts::SortedDataFrame; in_dates_period::Bool = true)
```

`SortedDataFrame`内の最初のティックと最後のティックの間の経過時間。

### 入力

  * `ts` - ティックデータ。
  * `in_dates_period` - Dates.Period形式または最初と最後のティックの間の数値的差を示す単なる数値。

### 返り値

  * この期間を表すスカラー。
