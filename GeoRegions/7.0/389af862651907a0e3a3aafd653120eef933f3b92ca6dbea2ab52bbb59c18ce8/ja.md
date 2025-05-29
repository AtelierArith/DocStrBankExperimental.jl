```
add(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    verbose :: Bool = false
) -> nothing
```

GeoRegion `geo` の情報を `path` で指定されたディレクトリに保存します。

# 引数

  * `geo` : `path` にカスタムリストとして保存される GeoRegion。

# キーワード引数

  * `path` : カスタム GeoRegions のリストが取得されるパス。デフォルトは `local` パッケージ変数 `geodir`。
  * `verbose` : 監視を容易にするための詳細なログ？ デフォルトは `false`。
