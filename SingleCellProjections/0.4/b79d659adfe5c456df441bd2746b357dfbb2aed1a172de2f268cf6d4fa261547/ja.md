```
NormalizationModel(data::DataMatrix, design::DesignMatrix;
                   scale=false, min_std=1e-6, annotate=true,
                   rtol=sqrt(eps()), var=:copy, obs=:copy)
```

`data` と `design` 行列に基づいて NormalizationModel を作成します。

  * `scale` - 変数を単位標準偏差に正規化するには true に設定します。各変数のスケーリングファクターを持つベクトルに設定することもできます。
  * `min_std` - `scale==true` の場合、`scale` ベクトルは `1.0 ./ max.(std, min_std)` に設定されます。つまり、`min_std` は非常に小さい変数を抑制するために使用されます（および、あらゆる変動はノイズであると見なすことができます）。
  * `annotate` - `scale!=false` の場合のみ使用されます。`annotate=true` の場合、`scale` ベクトルが変数の注釈として追加されます。
  * `rtol` - 設計行列の特異値が `≤rtol` の場合は破棄されます。数値的安定性のために必要です。
  * `var` - `:copy`（ソース `var` のコピーを作成）または `:keep`（ソース `var` オブジェクトを共有）にできます。
  * `obs` - `:copy`（ソース `obs` のコピーを作成）または `:keep`（ソース `obs` オブジェクトを共有）にできます。

参照: [`normalize_matrix`](@ref), [`designmatrix`](@ref)
