```
mask(w::GridData,surface::Body,grid::PhysicalGrid)
```

サーフェス `surface` の内部（すなわち、法線ベクトルの反対側）に1、外部に0を含むグリッドデータを作成します。グリッドデータは `w` と同じタイプです。
