```
DataDiGraph{T, T1, T2, T3, M1, M2}
```

数値データをノードおよび/またはエッジに含む有向グラフを構築および保存するためのオブジェクトです。

DataDiGraphには以下の属性があります:  `g`: Graphs.SimpleDiGraph オブジェクト  `nodes`: ノード名のベクター; ノード名は `Any` 型  `edges`: エッジのベクター; エッジは整数のタプル  `node_map`: ノード名をノード番号に指す辞書  `edge_map`: タプル (node*name1, node*name2) を (node*number1, node*number2) に指す辞書  `node_data`: 属性とデータを持つ NodeData オブジェクト  `edge_data`: 属性とデータを持つ EdgeData オブジェクト  `graph_data`: 属性とデータを持つ GraphData オブジェクト
