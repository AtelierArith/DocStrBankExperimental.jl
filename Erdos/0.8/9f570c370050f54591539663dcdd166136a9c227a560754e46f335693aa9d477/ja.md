```
digraph(s::Symbol, G = DiGraph)
```

タイプ `G` の悪名高い有向グラフ `s` を作成します。 `s` に対する許可される値は次のとおりです：

| `s`                   | グラフタイプ                                                                 |
|:--------------------- |:---------------------------------------------------------------------- |
| :truncatedtetrahedron | [切頭四面体有向グラフ](https://en.wikipedia.org/wiki/Truncated_tetrahedron) の骨格。 |
