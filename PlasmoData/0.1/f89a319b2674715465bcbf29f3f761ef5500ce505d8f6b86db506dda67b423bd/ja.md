```
get_path(datagraph, src_node, intermediate_node, dst_node; algorithm = "Dijkstra")
```

`src_node`と`dst_node`の間で`intermediate node`を通過する`datagraph`内の最短経路を返します。

`algorithm`は文字列のキーワードです。オプションは「Dijkstra」、「BellmanFord」に制限されています。
