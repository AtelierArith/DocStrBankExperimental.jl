```
struct ExchangeGraph{A}
```

交換に使用される有向グラフを表す型で、関数 [`exchange`](@ref) および [`exchange!`](@ref) を参照してください。

# プロパティ

  * `snd::A`
  * `rcv::A`

`snd[i]` にはノード `i` の出て行く隣接ノードのリストが含まれています。`rcv[i]` にはノード `i` の入ってくる隣接ノードのリストが含まれています。`A` はベクターのようなコンテナ型です。

# スーパタイプ階層

```
ExchangeGraph <: Any
```
