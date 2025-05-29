nested*column*to_array(df, var)

DataFrameの列からベクトル、行列、または配列を作成します。

```julia
nested_column_to_array(df, var)

```

### 必要な引数

```julia
* `df::DataFrame` : DataFrame
* `var::::Union{Symbol, String}` : DataFrame内の列
```

これは、以前利用可能だった`matrix()`関数の一般化です。

エクスポート済み
