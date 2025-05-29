```
compute_boundary_trans(d::DataDomain, perm)
```

境界半面透過率を perm に対して計算します。入力 `perm` は、`Cells()` に定義されたデータのシンボル、各セルの数値のベクトル、またはセルの数と同じ列数を持つ行列のいずれかです。
