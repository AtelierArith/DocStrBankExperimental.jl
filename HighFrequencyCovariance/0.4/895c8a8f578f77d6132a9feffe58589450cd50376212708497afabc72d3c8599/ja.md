```
default_spacing(
    ts::SortedDataFrame;
    rough_guess_number_of_intervals::Integer = 5,
    T::Real = duration(ts; in_dates_period = false),
)
```

リターン間のデフォルトの間隔を計算します。これは、Zhang, Mykland, Ait-Sahalia 2005のセクション1.2.3の式から来ています。

### 入力

  * `ts` - ティックデータ。
  * `rough_guess_number_of_intervals` - ティックデータを分割する間隔の数の粗い推定値。これは、最適な間隔を推定するための最初のパスで使用されます。
  * `T` - ティックデータの期間。

### 戻り値

  * 最適な間隔を表すスカラー。
