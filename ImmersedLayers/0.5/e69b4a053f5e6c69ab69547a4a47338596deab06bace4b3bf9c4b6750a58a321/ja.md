```
mask!(w::GridData,surface::Body,grid::PhysicalGrid)
```

データ `w` を、サーフェス `surface` 内部（すなわち、法線ベクトルの反対側）では1で、外部では0で掛け算することによって、その場でマスクします。
