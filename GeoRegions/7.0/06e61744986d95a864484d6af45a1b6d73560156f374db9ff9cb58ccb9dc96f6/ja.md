```
overwrite(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    verbose :: Bool = false
) -> nothing
```

ID `geo.ID` に関連付けられた既存の情報を `path` に上書きし、`geo` で指定された `GeoRegion` からの新しい情報で置き換えます。

# 引数

  * `geo` : `path` のカスタムリストに保存される `GeoRegion` で、ID `geo.ID` に関連付けられた既存の情報を上書きします。

# キーワード引数

  * `path` : カスタム GeoRegions のリストが取得されるパス。デフォルトは `local` パッケージ変数 `geodir` です。
  * `verbose` : 監視を容易にするための詳細なログ？ デフォルトは `false` です。
