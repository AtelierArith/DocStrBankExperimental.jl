```
==(
    geo1 :: GeoRegion,
    geo2 :: GeoRegion,
) -> tf :: Bool
```

異なる2つのGeoRegionのすべてのフィールド（名前とパスを除く）をチェックして、それらが完全に同じであるかどうかを判断します。GeoRegionは同じGeoRegion `type`でなければなりません。

`geo1.shape`と`geo2.shape`は、同じ領域を定義している限り、正確に同じである必要はありません（つまり、`geo2`の点は`geo1`の循環シフト版である可能性があります）。

# 引数

  * `geo1` : 最初のGeoRegion。
  * `geo2` : 2番目のGeoRegion。

# 戻り値

  * `tf` : `true`/`false`のブール値。
