`EnsembleParameterTable`は、アンサンブル構造方程式モデルの仕様を含みます。

# コンストラクタ

```
(1) EnsembleParameterTable(graph; observed_vars, latent_vars, groups)

(2) EnsembleParameterTable(ps::Pair...; param_labels = nothing)
```

(1) グラフまたは (2) 複数の仕様から構築された `EnsembleParameterTable` を返します。

# 引数

  * `graph`: `@StenoGraph` を介して定義されたグラフ
  * `observed_vars::Vector{Symbol}`: 観測変数名
  * `latent_vars::Vector{Symbol}`: 潜在変数名
  * `param_labels::Vector{Symbol}`: (オプション) パラメータ名のベクトル
  * `ps::Pair...`: `:group_name => specification`、ここで `specification` は `ParameterTable` または `RAMMatrices` のいずれかです。

# 例

[Multigroup models](@ref) に関するオンラインドキュメントを参照してください。
