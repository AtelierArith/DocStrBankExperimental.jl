```
get_assets(ts::SortedDataFrame, obs_to_include::Integer = 10)
```

これは、`SortedDataFrame`内のすべての資産のベクトルを返します。デフォルトでは、少なくともいくつかの観測値（デフォルトは10）が必要です。

### 入力

  * `ts` - ティックデータ。
  * `obs_to_include` - 関数がその資産を含めるために必要な`ts`内の最小ティック数を示す整数。

### 返り値

  * 各資産を含む`Vector{Symbol}`。
