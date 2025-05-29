```
rm(
    geo  :: GeoRegion;
    path :: AbstractString = geodir
) -> nothing
```

GeoRegion `geo` を `path` で指定されたカスタムリストから削除します。GeoRegion はカスタムリストにあるものと全く同じプロパティを持っている必要があります。

# 引数

  * `geo` : `path` のカスタムリストから削除される GeoRegion。

# キーワード引数

  * `path` : カスタム GeoRegions のリストが取得されるパス。デフォルトは `local` パッケージ変数 `geodir` です。
