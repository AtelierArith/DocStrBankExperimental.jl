```
getgraph(g::GNNGraph, i; nmap=false)
```

`g`によって誘導される部分グラフを返します。これは、`g.graph_indicator[j] == i`であるノード`j`、または`i`がコレクションである場合、`g.graph_indicator[j] ∈ i`を満たすノードです。言い換えれば、バッチグラフからコンポーネントグラフを抽出します。

`nmap=true`の場合、新しいノードを古いノードにマッピングするベクトル`v`も返します。部分グラフ内のノード`i`は、`g`内のノード`v[i]`に対応します。
