```
mask!(w::GridData,cache::BasicILMCache)
mask!(w::GridData,sys::ILMSystem)
```

データ `w` を、表面内で 1 で乗算し（すなわち、法線ベクトルの反対側で）、外側では 0 で乗算することによって、インプレースでマスクします。グリッドデータ `w` は、`cache` の出力データ型と同じ型でなければなりません。`cache` には `GridScaling` のみを許可します。
