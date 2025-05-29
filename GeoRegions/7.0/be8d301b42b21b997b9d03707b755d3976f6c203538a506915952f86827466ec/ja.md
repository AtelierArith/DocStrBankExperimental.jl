```
isgeo(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    strict  :: Bool = true,
    throw   :: Bool = true,
    verbose :: Bool = false
) -> tf :: Bool
```

プロジェクトで定義されたすべてのGeoRegionを`path`によって確認します。`GeoRegion` `geo`と同じ`ID` **かつ** 同じフィールド値（`name`と`path`を除く）を持つ`GeoRegion`が存在する場合、`true`を返します。そうでなければ、`false`を返すか、エラーをスローします。

# 引数

  * `geo` : 問題のGeoRegion。

# キーワード引数

  * `path` : カスタムGeoRegionのリストを取得するパス。デフォルトは`geo.path`のディレクトリです。
  * `strict` : `true`（デフォルト）であれば、`name`と`path`を除いてすべてのフィールドが同等であるかを確認します。
  * `throw` : `true`の場合、`path`に`geo`と同じ特性またはフィールド値を持つ`GeoRegion`が定義されていない場合にエラーをスローします。
  * `verbose` : 監視を容易にするための冗長なログ？デフォルトは`false`です。

# 戻り値

  * `tf` : `true`/`false`のブール値。
