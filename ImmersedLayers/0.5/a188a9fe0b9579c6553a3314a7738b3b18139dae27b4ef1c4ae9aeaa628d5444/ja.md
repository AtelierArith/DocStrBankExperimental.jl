```
complementary_mask!(w::GridData,surface::Body,grid::PhysicalGrid)
```

データ `w` を、表面 `surface` の内側（すなわち、法線ベクトルの反対側）で 0 で乗算し、外側で 1 で乗算することによって、インプレースでマスクします。
