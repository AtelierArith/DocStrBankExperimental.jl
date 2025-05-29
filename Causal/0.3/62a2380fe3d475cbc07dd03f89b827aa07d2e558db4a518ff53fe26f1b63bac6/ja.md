```julia
struct Node{CP, L}
```

モデル `Node` を `component` で構築します。 `idx` はインデックスで、`label` は `Node` のラベルです。

# フィールド

  * `component::Any`: ノードコンポーネント
  * `idx::Int64`: ノードインデックス
  * `label::Any`: ノードラベル
