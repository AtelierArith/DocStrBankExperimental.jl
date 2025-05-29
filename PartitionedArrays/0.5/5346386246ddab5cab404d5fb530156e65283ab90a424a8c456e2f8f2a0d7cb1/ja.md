```
assembly_graph(index_partition;kwargs...)
```

`index_partition`で定義された分散ベクトルのアセンブリに必要な通信グラフを表す[`ExchangeGraph`](@ref)のインスタンスを返します。`kwargs`は、送信者から受信者の隣接ノードを見つけるために[`ExchangeGraph`](@ref)に委譲されます。

次のように同等です。

```
neighbors = assembly_neighbors(index_partition;kwargs...)
ExchangeGraph(neighbors...)
```
