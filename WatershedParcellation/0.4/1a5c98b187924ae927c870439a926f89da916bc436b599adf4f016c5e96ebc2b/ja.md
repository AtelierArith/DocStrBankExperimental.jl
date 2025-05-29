```
find_minima(metric, surface; radius = 3)
```

行列 `metric`（勾配行列など）を与えられたとき、サイズ `radius` ステップのウィンドウ内で局所的な最小値を見つけます。引数 `surface <: SurfaceSpace` は、シンボル `:A`（隣接行列）を含む必要があります。
