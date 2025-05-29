```
edge_index(g::GNNGraph)
```

`g`内の各エッジのソースノードとターゲットノードをそれぞれ格納した2つのベクターを含むタプルを返します。

```julia
s, t = edge_index(g)
```
