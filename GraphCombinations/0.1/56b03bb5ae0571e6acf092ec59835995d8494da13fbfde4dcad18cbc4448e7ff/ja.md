```
canonical_form(graph::GraphRep, internal_indices::UnitRange{Int})::GraphRep
```

内部頂点の置換に基づくグラフの標準表現を見つけます。標準形は、`internal_indices`の置換を通じて達成可能な辞書順で最小のグラフ表現です。
