# errorbars_draws

ドロー（DataFrameの列）に対するエラーバーDataFrameを計算します。

```julia
errorbars_draws(df)
errorbars_draws(df, p)

```

## 必要な引数

  * `df`: DataFrame

# `p = [0.055, 0.945]`: 確率の境界

## 結果

`parameters`列を持つDataFrame

エクスポートされました。
