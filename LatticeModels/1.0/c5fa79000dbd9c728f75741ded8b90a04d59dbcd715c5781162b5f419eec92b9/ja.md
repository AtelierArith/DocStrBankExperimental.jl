```
Polygon{N}([半径, 中心])
Polygon{N}([中心; h])
```

与えられた（外接）半径と中心を持つ正規の `N` 辺の多角形を構築します。エイリアスに注意してください：`Triangle`、`Square`、および `Hexagon` はそれぞれ `Polygon{3}`、`Polygon{4}`、および `Polygon{6}` です。

## 引数

  * `半径`: 多角形の（外接）半径。
  * `中心`: 多角形の中心。

## キーワード引数

  * `h`: 中心から頂点までの距離。指定された場合、`半径` は `h / cos(pi / N)` として計算されます。
