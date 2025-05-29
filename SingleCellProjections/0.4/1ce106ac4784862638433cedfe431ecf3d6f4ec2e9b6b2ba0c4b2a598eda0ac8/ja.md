```
designmatrix(data::DataMatrix, [covariates...]; center=true, max_categories=100)
```

`data.obs` と指定された `covariates` からデザインマトリックスを作成します。共変量は文字列（data.obs の列名）を使用して指定でき、自動的に共変量が数値かカテゴリカルかを検出します。また、より詳細な制御のために `covariate` 関数を使用することもできます。

  * `center` - `true` の場合、デザインマトリックスに切片が追加されます。（非常に稀な状況でのみ `false` に設定すべきです。）
  * `max_categories` - 安全パラメータで、カテゴリが多すぎる場合はエラーが発生します。この場合、共変量がカテゴリカル共変量として使用されたのは間違いである可能性が高いです。非常に多くのカテゴリを使用することは、パフォーマンスやメモリ消費にも悪影響を及ぼします。

# 例

センタリングのみ:

```julia
julia> designmatrix(data)
```

切片付きの回帰モデル（センタリング）と "fraction_mt"（数値的注釈）:

```julia
julia> designmatrix(data, "fraction_mt")
```

上記と同様ですが、"batch"（カテゴリカル注釈）も含める:

```julia
julia> designmatrix(data, "fraction_mt", "batch")
```

参照: [`normalize_matrix`](@ref), [`NormalizationModel`](@ref), [`covariate`](@ref)
