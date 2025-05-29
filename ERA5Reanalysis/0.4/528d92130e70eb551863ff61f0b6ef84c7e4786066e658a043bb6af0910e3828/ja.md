```
isinERA5Region(
    geo    :: GeoRegion,
    e5geo  :: ERA5Region;
    domask :: Bool = false,
    throw  :: Bool = true
) -> Bool
```

`geo`で定義された子GeoRegionがERA5Region `e5geo`内にあるかどうかを確認します。

# 引数

  * `geo`   : ERA5Region `e5geo`によって定義された「子」またはサブセットであると仮定されるGeoRegion
  * `e5geo` : GeoRegion `geo`を含む「親」であると仮定されるERA5Region

# キーワード引数

  * `throw`  : `true`の場合、`geo`が`e5geo`内にないときにエラーが発生し、プログラムの実行が停止します
  * `domask` : `throw`が`false`で`domask`が`true`の場合、`geo`と`e5geo`が重ならない領域を示すマスク（`geo` GeoRegionによって定義された境界を持つ）を返します
