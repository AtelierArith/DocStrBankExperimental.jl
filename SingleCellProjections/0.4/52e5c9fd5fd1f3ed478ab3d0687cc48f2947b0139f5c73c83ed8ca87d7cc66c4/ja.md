```
var_counts_fraction!(counts::DataMatrix, sub_filter, tot_filter, col; check=true, var=:keep, obs=:keep)
```

各観測に対して、特定の変数パターンに一致するカウントの割合を計算します。

  * `sub_filter` はカウントされる変数を決定します。
  * `tot_filter` は合計に含める変数を決定します。

kwargs:

  * `var` - これを使用して `ProjectionModel` の `var` を設定します。
  * `obs` - これを使用して `ProjectionModel` の `obs` を設定します。`counts.obs` は `obs` の値に関係なく、その場で変更されることに注意してください。

`check=true` の場合、パターンに一致する変数がないとエラーが発生します。

フィルタリング構文の詳細については、以下の例と [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) のドキュメントを参照してください。

# 例

"Gene Expression" 特徴のみを考慮して、MT- 遺伝子のリードの割合を計算します（例えば "Antibody Capture" は含まれません）。

```
var_counts_fraction!(counts, "name"=>startswith("MT-"), "feature_type"=>isequal("Gene Expression"), "fraction_mt")
```

`feature_type` アノテーションがない場合（すなわち、すべての変数が遺伝子である場合）に、MT- 遺伝子のリードの割合を計算します。

```
var_counts_fraction!(counts, "name"=>startswith("MT-"), Returns(true), "fraction_mt")
```

参照: [`var_counts_fraction`](@ref)
