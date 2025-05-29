```
subset_to_time(ts::SortedDataFrame, totime::Real)
```

これは、`SortedDataFrame`を特定の時間までの最初の観測値のみを含むようにサブセットします。

### 入力

  * `ts` - ティックデータ。
  * `totime` - どの時間まで。

### 返り値

  * （より小さい）`SortedDataFrame`。
