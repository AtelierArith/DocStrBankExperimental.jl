```
Transformer(dim, n_heads, L)
```

次元 `dim` と `L` ブロックのために `n_heads` を持つ Transformer のインスタンスを作成します。

# 引数

`Transformer` は以下のオプションキーワード引数を取ります：

  * `activation = tanh`: [`ResNetLayer`](@ref) に使用される活性化関数。
  * `Stiefel::Bool = false`: 行列 $P^V$, $P^Q$ および $P^K$ が多様体上に存在するべきかどうか。
  * `add_connection::Bool = false`: 入力が [`MultiHeadAttention`](@ref) レイヤーの後に出力に追加されるべきかどうか。
  * `use_bias::Bool = true`: [`ResNetLayer`](@ref) がバイアスを使用するかどうかを指定します。
