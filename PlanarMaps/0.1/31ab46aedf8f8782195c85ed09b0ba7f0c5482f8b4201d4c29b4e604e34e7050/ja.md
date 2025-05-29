```
draw(P,outeredge,corners)
```

平面地図 P を描画します。外側の面は次のいずれかです：     - `outeredge` の左側にある面     - 頂点の列 `corners` を含む面

  * `outeredge` は順序付きペアです
  * `corners` は `nothing`（`outeredge` による仕様への従属を示す）または順序付き三重項です
