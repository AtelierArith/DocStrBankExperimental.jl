```
get_path(datagraph, src_node, dst_node; algorithm = "Dijkstra")
```

`src_node`と`dst_node`の間の`datagraph`内の最短経路を返します。最短経路はダイクストラのアルゴリズムによって計算されます。

`algorithm`は文字列のキーワードです。オプションは「Dijkstra」と「BellmanFord」に制限されています。
