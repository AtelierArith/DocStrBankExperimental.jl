```
mask!(w::GridData,surface::Body,grid::PhysicalGrid)
```

データ `w` を、サーフェス `surface` 内部（すなわち、法線ベクトルの反対側）では 1 で、外部では 0 で掛け算することによって、その場でマスクします。
