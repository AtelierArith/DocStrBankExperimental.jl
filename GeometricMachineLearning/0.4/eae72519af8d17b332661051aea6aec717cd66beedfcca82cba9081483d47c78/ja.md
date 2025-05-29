```
MultiHeadAttention(dim, n_heads)
```

次元 `dim` のシステムに対して `n_heads` を持つ `MultiHeadAttention` レイヤーを作成します。

`dim` は `n_heads` で割り切れる必要があることに注意してください。

MultiHeadAttention (MHA) はトランスフォーマーの前処理ステップとして機能します。

それはデータ内の相関に基づいて入力ベクトルの重みを再調整します。

これはニューラルネットワーク [`StandardTransformerIntegrator`](@ref) と [`ClassificationTransformer`](@ref) に使用されます。

# 引数

`MultiHeadAttention` に対するオプションのキーワード引数は次のとおりです：

  * `Stiefel::Bool=false`
  * `add_connection::Bool=true`
  * `activation::AbstractSoftmax=`[`VectorSoftmax`](@ref)。

`Stiefel` は、重みが [`StiefelManifold`](@ref) $St(\mathrm{dim}, \mathrm{dim}\div\mathrm{n\_heads})$ に置かれるかどうかを示します。

`add_connection` は、入力が出力に再度加算されるかどうかを示します。
