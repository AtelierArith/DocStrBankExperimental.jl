```
addGeoRegions(
    fname :: AbstractString;
    path  :: AbstractString = pwd(),
    overwrite :: Bool = false,
    verbose   :: Bool = false
) -> nothing
```

ファイル `fname` から GeoRegions をプロジェクトディレクトリに追加します。`path` で定義されています。

# 引数

  * `fname` : GeoRegion 情報を含むファイルの名前 + パス。

# キーワード引数

  * `path` : カスタム GeoRegions のリストが取得されるパス。デフォルトは現在の作業ディレクトリ `pwd()` です。
  * `overwrite` : `true` の場合、ファイル `fname` にあるのと同じ `ID` を持つカスタム GeoRegions を上書きします。
