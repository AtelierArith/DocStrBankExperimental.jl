```
complementary_mask(w::GridData,surface::Body,grid::PhysicalGrid)
```

サーフェス `surface` の内部（すなわち法線ベクトルの反対側）には 0、外部には 1 からなるグリッドデータを作成します。グリッドデータは `w` と同じ型です。
