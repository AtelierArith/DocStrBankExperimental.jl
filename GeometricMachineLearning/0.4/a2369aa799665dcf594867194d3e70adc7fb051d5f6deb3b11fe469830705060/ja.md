```
StandardTransformerIntegrator(sys_dim)
```

特定のシステム次元のために `StandardTransformerIntegrator` のインスタンスを作成します。

ここで、統合器として使用される標準トランスフォーマー（[`TransformerIntegrator`](@ref)を参照）。 

これは、[`MultiHeadAttention`](@ref) レイヤーと [`ResNetLayer`](@ref) レイヤーの構成です。

# 引数

以下はオプションのキーワード引数です：

  * `transformer_dim::Int = sys_dim`: これは *アップスケーリング後の* 次元です。
  * `n_blocks::Int = 1` : [`ResNetLayer`](@ref) ブロックの数。
  * `n_heads::Int = sys_dim`: マルチヘッドアテンションレイヤーのヘッドの数。
  * `L::Int = 2`: トランスフォーマーブロックの数。
  * `upscaling_activation = identity`: アップスケーリングレイヤーで使用される活性化。
  * `resnet_activation = tanh`: [`ResNetLayer`](@ref) 用の活性化。
  * `attention_activation = GeometricMachineLearning.VectorSoftmax()` : [`MultiHeadAttention`](@ref) レイヤーで使用される活性化。
  * `add_connection:Bool = true`: 入力を出力に追加するかどうかを指定します。
