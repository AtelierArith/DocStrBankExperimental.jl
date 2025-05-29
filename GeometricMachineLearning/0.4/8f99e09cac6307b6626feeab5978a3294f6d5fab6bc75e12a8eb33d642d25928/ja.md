```
ClassificationTransformer(dl)
```

[`DataLoader`](@ref) のインスタンスに基づいて `ClassificationTransformer` のインスタンスを作成します。

これは分類目的のためのトランスフォーマーニューラルネットワークです。現時点ではMNISTのトレーニングにのみ使用されていますが、理論的には任意の分類問題に使用できます。

# 引数

オプションのキーワード引数は次のとおりです：

  * `n_heads::Int=7`: `MultiHeadAttention` (mha) レイヤーのヘッドの数。
  * `L::Int=16`: トランスフォーマーブロックの数。
  * `activation=softmax`: 活性化関数。
  * `Stiefel::Bool=true`: mha レイヤーの行列が [`StiefelManifold`](@ref) 上にあるかどうか。
  * `add_connection::Bool=true`: 入力が mha レイヤーの出力に追加されるかどうか。（スキップ接続）
