```
ellipsePts(f1, f2; percent=0.95, nPoints=500)
```

`f1` と `f2` のデータエリプスの周囲の `nPoints` 点を計算します。エリプス内には `percent` で指定されたデータの約パーセントが含まれます。点は、極座標の回転角が 0 から 2π に移動するにつれて反時計回りの順序で返されます。

計算プロセスの詳細については、Friendly, Monette, and Fox (2013, Elliptical insights: Understanding statistical methods through elliptical geometry, Statistical science 28(1), 1-39) を参照してください。

# 引数

  * `f1` F1 値または x 軸の値
  * `f2` F2 値または y 軸の値
  * `percent` (キーワード) エリプスが概ねカバーすべきデータ分布のパーセント
  * `nPoints` (キーワード) エリプスを描画する際に使用する点の数
