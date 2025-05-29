```
downstream_nodes(dg::DataDiGraph, node; algorithm = "bfs")
```

`dg`のDataDiGraph内の`node`の下流にあるすべてのノードのリストを返します。アルゴリズムのオプションは「bfs」と「dfs」です。
