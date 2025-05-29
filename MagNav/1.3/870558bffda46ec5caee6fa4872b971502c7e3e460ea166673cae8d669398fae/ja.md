```
map_interpolate(mapV::MapV, dim::Symbol = :X, type::Symbol = :cubic)
```

マップ補間関数を作成します。これはMATLABのgriddedInterpolantに相当します。

**引数:**

  * `mapV`: `MapV`ベクトル磁気異常マップ構造体
  * `dim`: 補間するマップの次元 {`:X`,`:Y`,`:Z`}
  * `type`: (オプション) 補間の種類 {:linear,:quad,:cubic}

**戻り値:**

  * `itp_map`: マップ補間関数 (`f(yy,xx)`)
