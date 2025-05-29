```
subset_to_tick(ts::SortedDataFrame, n::Integer)
```

これは `SortedDataFrame` を最初の n 個のティックのみにサブセットします。

### 入力

  * `ts` - ティックデータ。
  * `n` - サブセットするティックの数。

### 返り値

  * （小さい）`SortedDataFrame`。
