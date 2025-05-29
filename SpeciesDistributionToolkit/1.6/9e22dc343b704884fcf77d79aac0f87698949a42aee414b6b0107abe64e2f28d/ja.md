```
byzone(f, layer::SDMLayer, polygons, polygonsnames = 1:length(polygons))
```

関数 `f` を同じポリゴンに属するすべてのセルに適用し、出力を辞書として返します。引数として与えられた関数は、位置引数とキーワード引数の両方を受け取ることができます。
