```
isgeoshape(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    returnID :: Bool = true,
    verbose  :: Bool = false
) -> tf :: Bool
```

プロジェクトで定義されたすべてのGeoRegionを、`path`によって決定された場所でチェックします。`geo.shape`と同じ形状の`GeoRegion`が存在する場合、デフォルトで`true`を返します。そうでない場合、`returnID`が`true`であればIDを返します。同じ形状の`GeoRegion`が存在しない場合、`false`を返すか、`throw`に応じてエラーをスローします。

# 引数

  * `geo` : 問題のGeoRegion。

# キーワード引数

  * `path` : GeoRegionsが取得され、比較されるパス。デフォルトは`geo.path`のディレクトリです。
  * `returnID` : `true`の場合、`geo`と同じ形状の`path`内の`GeoRegion`の`ID`を返します。
  * `verbose` : 監視を容易にするための詳細なログ？デフォルトは`false`です。

# 戻り値

  * `tf` : `true`/`false`のブール値。
