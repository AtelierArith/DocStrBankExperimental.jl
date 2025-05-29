```
sctransform(X::AbstractSparseMatrix, features, params;
            transpose = false,
            feature_id_columns = [:id,:feature_type],
            feature_type,
            feature_mask,
            cell_ind = 1:size(X,2),
            clip=sqrt(size(X,2)/30))
```

スパース行列 `X` の SCTransform を計算します。特徴量は行として、細胞は列として配置されます。`features` は特徴量の注釈を持つテーブル（例：DataFrame または NamedTuple）である必要があります。`params` は正則化された特徴量パラメータ推定値を持つテーブルであり、通常は `scparams` 関数を使用して推定されます。

  * `transpose` - 出力を転置するには true に設定します（細胞が行、特徴量が列）。
  * `feature_id_columns` は `features` の列名のベクターです。`features` の行はこれらの列に基づいて一意である必要があります。
  * `feature_type` - `feature_mask` のデフォルトに使用される便利なパラメータです。`features` に `feature_type` 列がある場合は "Gene Expression" にデフォルト設定されます。
  * `feature_mask` - 使用する特徴量を決定するブール値のベクターです。明示的に設定されている場合、`feature_type` パラメータは無視され、それ以外の場合は `feature_mask` は指定された `feature_type` のみを選択することにデフォルト設定されます。logcellcounts の計算方法に影響します。通常、`scparams` を呼び出す際に使用される `feature_mask` と一致することが期待されます。
  * `cell_ind` は出力に含める細胞インデックスのベクターです。これは後でサブセットするよりも計算効率が良いですが、同じ結果をもたらします。
  * `clip` - `-clip` より小さい値または `clip` より大きい値はクリップされ、外れ値の影響を減少させます。

参照： [`scparams`](@ref)
