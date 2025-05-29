```
ftest_table(data::DataMatrix, h1; h0, kwargs...)
```

与えられた `h1`（対立仮説）および `h0`（帰無仮説）を用いてF検定を実行します。F検定の例にはANOVAや二次回帰が含まれますが、任意の線形モデルを使用できます。（具体的な例については下の「例」を参照してください。）

F検定は任意の `DataMatrix` に対して実行できますが、データを `sctransform`、`logtransform`、または `tf_idf_transform` などを使用して変換した後に直接実行することがほぼ常に推奨されます。

!!! note "正規化"
    `normalize_matrix` を使用してデータを正規化した後に `ftest_table` を使用しないでください：`ftest_table` は補正計算のために `h0` モデル（回帰された共変量）について知っている必要があります。これを怠ると不正確な結果が得られる可能性があります。同じ共変量に対して補正を行いたい場合は、それらを `h0` として `ftest_table` に渡してください。


`h1` は次のように指定できます：

  * `data.obs` の列名を指定する文字列。自動検出により、その列がカテゴリカル（ANOVA）か数値的かが判断されます。
  * 列の値を解釈する方法をより制御するための [`covariate`](@ref)。
  * 複合モデルのための上記のタプルまたはベクトル。

`ftest_table` は変数ID、F統計量、およびp値の列を持つDataFrameを返します。

サポートされている `kwargs` は次のとおりです：

  * `h0`                  - 非自明な `h0`（帰無）モデルを使用します。上記の `h1` と同じ方法で指定します。
  * `center=true`         - `h0`（帰無）モデルに切片を追加します。
  * `statistic_col="F"`   - F統計量を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `pvalue_col="pValue"` - p値を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `h1_missing=:skip`    - `:skip` と `:error` のいずれか。`skip` の場合、`h1` 列の欠損値はスキップされ、それ以外の場合はエラーが発生します。
  * `h0_missing=:error`   - `:skip` と `:error` のいずれか。`skip` の場合、`h0` 列の欠損値はスキップされ、それ以外の場合はエラーが発生します。
  * `allow_normalized_matrix=false` - 正規化された `DataMatrix` での実行を受け入れるにはtrueに設定します。

# 例

"celltype" アノテーションを使用してANOVAを実行します。

```julia
julia> ftest_table(transformed, "celltype")
```

"celltype" アノテーションを使用してANOVAを実行し、`fraction_mt`（線形共変量）で補正します。

```julia
julia> ftest_table(transformed, "celltype"; h0="fraction_mt")
```

"celltype" アノテーションを使用してANOVAを実行し、`fraction_mt`（線形共変量）および "phase"（カテゴリカル共変量）で補正します。

```julia
julia> ftest_table(transformed, "celltype"; h0=("fraction_mt","phase"))
```

共変量 `x` を使用して二次回帰を実行し、最初に `x` の二乗のアノテーションを作成し、その後複合モデルを使用します。

```julia
julia> data.obs.x2 = data.obs.x.^2;

julia> ftest_table(transformed, ("x","x2"))
```

参照： [`ftest!`](@ref), [`ftest`](@ref), [`ttest_table`](@ref), [`covariate`](@ref)
