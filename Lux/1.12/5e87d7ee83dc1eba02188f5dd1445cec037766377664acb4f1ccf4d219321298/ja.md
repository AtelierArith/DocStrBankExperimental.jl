```
SimpleChainsLayer(layer, to_array::Union{Bool, Val}=Val(false))
SimpleChainsLayer(layer, lux_layer, to_array)
```

`SimpleChains` レイヤーを `Lux` レイヤーにラップします。すべての操作は `SimpleChains` を使用して実行されますが、このレイヤーは `AbstractLuxLayer` インターフェースを満たします。

`ToArray` は、出力を通常の `Array` に変換するかどうかを決定するブールフラグです。デフォルトは `false` です。

## 引数

  * `layer`: SimpleChains レイヤー
  * `lux_layer`: 印刷に使用される潜在的に同等の Lux レイヤー
