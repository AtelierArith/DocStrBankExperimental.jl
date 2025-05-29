```
CGConv((node_dim, edge_dim), init, bias=true)
```

クリスタルグラフ畳み込みネットワーク。ノードとエッジの特徴の両方を使用します。

# 引数

  * `node_dim`: 入力ノード特徴の次元。出力の次元でもあります。
  * `edge_dim`: 入力エッジ特徴の次元。
  * `init`: 各重み行列の初期化アルゴリズム
  * `bias`: 加算バイアスパラメータを学習するかどうか。

# 例

```jldoctest
julia> CGConv((128, 32))
CGConv(node dim=128, edge dim=32)
```

静的グラフでのトレーニングレイヤーについては、[`WithGraph`](@ref)も参照してください。
