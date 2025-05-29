```
isequal(
    geo1 :: GeoRegion,
    geo2 :: GeoRegion;
    strict  :: Bool = true,
    verbose :: Bool = false
) -> tf :: Bool
```

異なる2つのGeoRegionのすべてのフィールド（名前を除く）をチェックして、それらが完全に同じであるかどうかを判断します。GeoRegionは、同じ`ID`、`pID`、および`shape`で定義された面積を持っている限り、同じGeoRegion `type`である必要はありません。

`geo1.shape`と`geo2.shape`は、正確に同じである必要はなく、正確に同じ面積を定義している限り、`geo2`の点は`geo1`の`circshift()`バージョンであっても構いません。

# 引数

  * `geo1` : 最初のGeoRegion。
  * `geo2` : 2番目のGeoRegion。

# キーワード引数

  * `strict` : `true`（デフォルト）であれば、`geo1`と`geo2`は同じGeoRegion `type`でなければなりません（例：`RectRegion ≠ PolyRegion`）。
  * `verbose` : 監視を容易にするための詳細なログ？デフォルトは`false`です。

# 戻り値

  * `tf` : `true`/`false`のブール値。
