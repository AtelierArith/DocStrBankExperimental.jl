```
normalize_matrix(data::DataMatrix, [covariates...]; center=true, scale=false, kwargs...)
```

`data`を正規化します。デフォルトでは、行列は中心化されています。指定された任意の`covariates`（`data.obs`の列名を使用）を回帰させます。

  * `center` - データ行列を中心化するにはtrueに設定します。
  * `scale` - データ行列の変数を単位標準偏差にスケーリングするにはtrueに設定します。

その他の`kwargs`や詳細な説明については、`NormalizationModel`および`designmatrix`を参照してください。

# 例

中心化のみ:

```julia
julia> normalize_matrix(data)
```

切片付き回帰モデル（中心化）および「fraction_mt」（数値注釈）:

```julia
julia> normalize_matrix(data, "fraction_mt")
```

上記と同様ですが、「batch」（カテゴリカル注釈）も含める:

```julia
julia> normalize_matrix(data, "fraction_mt", "batch")
```

参照: [`NormalizationModel`](@ref), [`designmatrix`](@ref)
