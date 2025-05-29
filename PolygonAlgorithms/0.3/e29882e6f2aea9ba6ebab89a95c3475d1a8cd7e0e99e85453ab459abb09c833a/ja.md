```
convex_hull(points, alg=GiftWrappingAlg())
```

点の集合に対する凸包のインデックスを決定します。

`alg` は `GiftWrappingAlg()` または `GrahamScanAlg()` のいずれかです。

入力頂点が `n` で、凸包上の結果頂点が `h` の場合：

  * `GiftWrappingAlg` は `O(nh)` 時間で実行されます。
  * `GrahamScanAlg` は `O(n*log(n))` 時間で実行されます。
