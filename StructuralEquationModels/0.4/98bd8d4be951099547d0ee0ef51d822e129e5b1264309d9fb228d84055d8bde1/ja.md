`RAMMatrices`は構造方程式モデルの仕様を含みます。

# コンストラクタ

```
(1) RAMMatrices(partable::ParameterTable; param_labels = nothing)

(2) RAMMatrices(;A, S, F, M = nothing, param_labels, vars = nothing)

(3) RAMMatrices(partable::EnsembleParameterTable)
```

(1) パラメータテーブルから構築された `RAMMatrices` を返します。または (2) 個別の行列から構築された `RAMMatrices` を返します。

(3) `EnsembleParameterTable` からの `RAMMatrices` の辞書を返します（キーはグループ名です）。

# 引数

  * `partable`
  * `A`: 指向効果の行列
  * `S`: 無指向効果の行列
  * `F`: フィルタ行列
  * `M`: 平均効果のベクトル
  * `param_labels::Vector{Symbol}`: パラメータラベル
  * `vars::Vector{Symbol}`: A, S および F 行列の列に対応する変数名

# 例

[モデル仕様](@ref) および [RAMMatrices インターフェース](@ref) に関するオンラインドキュメントを参照してください。
