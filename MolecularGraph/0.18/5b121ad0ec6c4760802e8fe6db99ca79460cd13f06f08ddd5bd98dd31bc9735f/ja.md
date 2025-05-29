```
line_graph(G::SimpleGraph) -> SimpleGraph, Dict, Dict
```

線グラフを生成し、逆マッピング lg(v) -> g(e) と共有ノードマッピング lg(e) -> g(v) を作成します。
