```
var_counts_sum!([f=identity], counts::DataMatrix, filter, col; check=true, var=:keep, obs=:keep)
```

各観測に対して、`filter` に一致するカウントの合計を計算します。

`f` が指定されている場合、合計を計算する前に各要素に適用されます。（`sum` に似ています。）

kwargs:

  * `var` - これを使用して `ProjectionModel` の `var` を設定します。
  * `obs` - これを使用して `ProjectionModel` の `obs` を設定します。`counts.obs` は、`obs` の値に関係なく、その場で変更されることに注意してください。

`check=true` の場合、パターンに一致する変数がないとエラーが発生します。

フィルタリング構文の詳細については、以下の例と [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) に関するドキュメントを参照してください。

# 例

すべての "Gene Expression" カウントの合計:

```
var_counts_sum!(counts, "feature_type"=>isequal("Gene Expression"), "totalRNACount")
```

表現されている "Gene Expression" 変数の数を計算します（すなわち、ゼロ以外）:

```
var_counts_sum!(!iszero, counts, "feature_type"=>isequal("Gene Expression"), "nonzeroRNACount")
```

参照: [`var_counts_sum`](@ref)
