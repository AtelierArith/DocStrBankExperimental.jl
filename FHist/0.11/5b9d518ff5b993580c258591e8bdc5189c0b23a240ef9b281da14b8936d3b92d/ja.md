```
project(h::Hist3D, axis::Symbol=:x)
project(axis::Symbol=:x) = h::Hist3D -> project(h, axis)
```

3Dヒストグラムの`:x`/`:y`/`:z`軸の投影を、指定された軸に沿って合計することで計算します。`Hist2D`を返します。
