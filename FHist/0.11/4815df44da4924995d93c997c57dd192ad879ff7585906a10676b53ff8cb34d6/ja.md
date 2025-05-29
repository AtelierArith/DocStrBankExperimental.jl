```
project(h::Hist2D, axis::Symbol=:x)
project(axis::Symbol=:x) = h::Hist2D -> project(h, axis)
```

2D ヒストグラムの `:x` (`:y`) 軸の投影を、y (x) 軸に沿って合計することによって計算します。`Hist1D` を返します。
