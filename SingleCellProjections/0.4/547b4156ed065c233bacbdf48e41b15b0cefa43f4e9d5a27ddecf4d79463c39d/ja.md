```
ttest_table(data::DataMatrix, h1, [group_a], [group_b]; h0, kwargs...)
```

与えられた `h1`（対立仮説）および `h0`（帰無仮説）を使用してt検定を実行します。t検定の例には、二群検定や線形回帰があります。

t検定は任意の `DataMatrix` に対して実行できますが、データを `sctransform`、`logtransform`、または `tf_idf_transform` などを使用して変換した後に直接実行することがほぼ常に推奨されます。

!!! note "正規化"
    `normalize_matrix` を使用してデータを正規化した後に `ttest_table` を使用しないでください：`ttest_table` は補正計算のために `h0` モデル（回帰された共変量）について知っている必要があります。これを怠ると不正確な結果が得られる可能性があります。同じ共変量に対して補正を行いたい場合は、それらを `h0` として `ttest_table` に渡してください。


`h1` は次のように指定できます：

  * `data.obs` の列名を指定する文字列。自動検出により、列がカテゴリカル（2群）か数値（線形回帰）かが判断されます。

      * `group_a` と `group_b` が指定されている場合、`group_a` と `group_b` の間で二群検定が実行されます。
      * `group_a` が指定されているが `group_b` が指定されていない場合、`group_a` と他のすべての観測値との間で二群検定が実行されます。
  * 列の値を解釈する方法をより制御するための [`covariate`](@ref)。

`ttest_table` は、変数ID、t統計量、p値、および差の列を持つデータフレームを返します。二群検定の場合、`difference` は2つの群の平均の差です。線形回帰の場合、差は変化率に対応します。

サポートされている `kwargs` は次のとおりです：

  * `h0`                            - 非自明な `h0`（帰無）モデルを使用します。上記の `h1` と同じ方法で指定します。
  * `center=true`                   - `h0`（帰無）モデルに切片を追加します。
  * `statistic_col="t"`             - t統計量を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `pvalue_col="pValue"`           - p値を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `difference_col="difference"`   - 差を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `h1_missing=:skip`              - `:skip` と `:error` のいずれか。`skip` の場合、`h1` 列の欠損値はスキップされ、それ以外の場合はエラーが発生します。
  * `h0_missing=:error`             - `:skip` と `:error` のいずれか。`skip` の場合、`h0` 列の欠損値はスキップされ、それ以外の場合はエラーが発生します。
  * `allow_normalized_matrix=false` - 正規化された `DataMatrix` での実行を受け入れるには true に設定します。

# 例

細胞タイプ "Mono" と "DC" の間で二群t検定を実行します。

```julia
julia> ttest_table(transformed, "celltype", "Mono", "DC")
```

細胞タイプ "Mono" と他のすべての細胞との間で二群t検定を実行します。

```julia
julia> ttest_table(transformed, "celltype", "Mono")
```

細胞タイプ "Mono" と "DC" の間で二群t検定を実行し、"fraction_mt"（線形共変量）で補正します。

```julia
julia> ttest_table(transformed, "celltype", "Mono", "DC")
```

共変量 "fraction_mt" を使用して線形回帰を実行します。

```julia
julia> ttest_table(transformed, "fraction_mt")
```

関連項目: [`ttest!`](@ref), [`ttest`](@ref), [`ftest_table`](@ref), [`mannwhitney_table`](@ref), [`covariate`](@ref) ```
