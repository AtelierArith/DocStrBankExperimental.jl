```
GeoRegion(
    ID :: AbstractString;
    path    :: AbstractString = homedir(),
    verbose :: Bool = false
) -> geo :: GeoRegion
```

ID `ID`を持つGeoRegionの情報を抽出します。このIDのGeoRegionが存在しない場合、エラーが発生します。

# 引数

  * `ID` : GeoRegionを識別するために使用されるIDです。           IDが無効な場合（すなわち、使用されていない場合）、エラーが発生します。

# キーワード引数

  * `path` : カスタムGeoRegionのリストが取得されるパスです。          デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `verbose` : 監視を容易にするための詳細なログです。デフォルトは`false`です。

# 戻り値

  * `geo` : GeoRegionです。
