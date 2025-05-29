```
tableGeoRegions(;
    path :: AbstractString = homedir(),
    predefined :: Bool = true,
    custom     :: Bool = true,
    warn :: Bool = true,
    crop :: Bool = false
) -> nothing
```

利用可能なGeoRegionsを表形式で表示します。

# キーワード引数

  * `path` : カスタムGeoRegionsのリストを取得するパス。デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `predefined` : `true`の場合、事前定義されたGiorgi、SREXおよびIPPC AR6のGeoRegionsリストが表示されます。
  * `custom` : `true`の場合、カスタムのユーザー定義GeoRegionsリストが表示されます。
  * `warn` : `true`の場合、カスタムファイルが存在しない場合に警告を表示します。
  * `crop` : `true`の場合、テーブルの垂直範囲を切り取ります。デフォルトは`false`です。
