空のプレースホルダーは、暗黙の部分を必要としないモデルのためのものです。（例えば、パラメータのみを正則化するモデル。）

# コンストラクタ

```
ImpliedEmpty(;specification, kwargs...)
```

# 引数

  * `specification`: `RAMMatrices` または `ParameterTable` オブジェクトのいずれか

# 例

リッジ正則化を持つマルチグループモデルは、グループごとに1つのモデルを持つ `SemEnsemble` と、正則化部分のための `ImpliedEmpty` と `SemRidge` を持つ追加のモデルとして指定できます。

# 拡張ヘルプ

## インターフェース

  * `param_labels(::ImpliedEmpty)`-> パラメータラベルのベクター
  * `nparams(::ImpliedEmpty)` -> パラメータの数
