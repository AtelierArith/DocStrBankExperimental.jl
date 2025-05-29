```
velocity_grids(xci, xvi, di::NTuple{N,T}) where {N,T}
```

N次元問題の速度グリッドを計算します。

# 引数

  * `xci`: セル中心のx座標。
  * `xvi`: セル頂点のx座標。
  * `di`: セルの次元を含むタプル。
