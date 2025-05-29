```
on(
    geo1 :: GeoRegion,
    geo2 :: GeoRegion;
    n    :: Int = 2,
    throw   :: Bool = false,
    verbose :: Bool = false
) -> tf :: Bool
```

`geo1` と `geo2` の GeoRegion が同じ形状を持っているかどうかを確認します。`geo1` と `geo2` の順序は関係ありません。

# 引数

  * `geo1` : 最初の GeoRegion
  * `geo2` : 2 番目の GeoRegion

# キーワード引数

  * `n` : 各 `GeoRegion` を分割するセグメントの数。デフォルトは 2 です。
  * `throw` : `true` の場合、`geo1` が `geo2` と同じ形状でない場合にエラーが発生し、プログラムの実行が停止します。
  * `verbose` : `true` の場合、ログを画面に表示します。

# 戻り値

  * `tf` : `true`/`false` のブール値。
