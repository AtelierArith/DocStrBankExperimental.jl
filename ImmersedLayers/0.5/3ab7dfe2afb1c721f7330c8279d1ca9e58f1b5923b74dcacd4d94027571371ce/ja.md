```
complementary_mask!(w::GridData,cache::BasicILMCache)
complementary_mask!(w::GridData,sys::ILMSystem)
```

データ `w` を、表面の内側（すなわち法線ベクトルの反対側）に0を掛け、外側に1を掛けることでインプレースでマスクします。グリッドデータ `w` は、`cache` の出力データ型と同じ型でなければなりません。`cache` は `GridScaling` のみを許可します。
