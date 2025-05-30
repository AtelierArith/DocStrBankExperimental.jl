```julia
struct TensorNetworkModel{ET, MT<:AbstractArray}
```

テンソルネットワークによる確率モデル。

### フィールド

  * `nvars` はテンソルネットワーク内の変数の数です。
  * `code` はテンソルネットワークの収束パターンです。
  * `tensors` はテンソルネットワークに供給されるテンソルで、先頭のテンソルは `unity_tensors_labels` に関連付けられた単位テンソルです。
  * `evidence` は特定の値に固定された自由度を指定するために使用される辞書です。
  * `unity_tensors_idx` は `tensors` 配列内の単位テンソルのインデックスのベクトルです。単位テンソルは周辺確率を取得するために使用されるダミーテンソルです。
