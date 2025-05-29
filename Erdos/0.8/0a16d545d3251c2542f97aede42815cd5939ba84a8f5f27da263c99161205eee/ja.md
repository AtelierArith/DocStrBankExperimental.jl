```
subgraph(g, vlist) -> sg, vlist
subgraph(g, elist) -> sg, vlist
```

`g`の頂点`vlist`によって誘導される部分グラフを返すか、`elist`のエッジによって誘導される部分グラフを返し、`vlist`自体（2番目の方法のために新しく作成されたベクトル）を返します。

返されるグラフは`length(vlist)`の頂点を持ち、新しい頂点`i`は`vlist`の`i`番目の位置にある元のグラフの頂点に対応します。

簡単に部分グラフを作成するために、`g[vlist]`や`g[elist]`も使用できます。

`g`がネットワークである場合、ベクトルおよびエッジのプロパティは`sg`に引き継がれません。プロパティを保持するには、[`subnetwork`](@ref)メソッドを使用できます。

### 使用例:

```julia
g = CompleteGraph(10)
sg, vlist = subgraph(g, 5:8)
@assert g[5:8] == sg
@assert nv(sg) == 4
@assert ne(sg) == 6
@assert vm[4] == 8

sg, vlist = subgraph(g, [2,8,3,4])
@asssert sg == g[[2,8,3,4]]

elist = [Edge(1,2), Edge(3,4), Edge(4,8)]
sg, vlist = subgraph(g, elist)
@asssert sg == g[elist]
```
