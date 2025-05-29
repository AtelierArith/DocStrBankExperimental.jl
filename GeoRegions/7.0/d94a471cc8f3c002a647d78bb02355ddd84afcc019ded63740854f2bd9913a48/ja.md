```
in(
    cgeo :: GeoRegion,
    geo  :: GeoRegion;
    n    :: Int = 100,
    throw   :: Bool = false,
    verbose :: Bool = false
) -> tf :: Bool
```

`cgeo`で定義された子のGeoRegionが、別のGeoRegion `geo`の中にあるかどうかを確認します。

# 引数

  * `cgeo` : 私たちが「子」と考えるGeoRegion、または`geo`で定義されたGeoRegionのサブセット。
  * `geo` : 私たちが「親」と考えるGeoRegion、または`cgeo`で定義されたGeoRegionを含むGeoRegion。

# キーワード引数

  * `n` : 各`GeoRegion`を分割するセグメントの数。デフォルトは100。
  * `throw`  : `true`の場合、`cgeo`が`geo`の中にないときにエラーが発生し、プログラムの実行が停止します。
  * `verbose` : `true`の場合、ログを画面に表示します。

# 戻り値

  * `tf` : `true`/`false`のブール値。
