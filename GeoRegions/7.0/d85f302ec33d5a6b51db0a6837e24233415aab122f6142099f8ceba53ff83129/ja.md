```
setupGeoRegions(;
    path :: AbstractString = pwd(),
    overwrite :: Bool = false
) -> nothing
```

指定された`path`ディレクトリにカスタム`GeoRegion`用のファイルをセットアップします。`overwrite = true`の場合、既存のファイルは上書きされます。

# キーワード引数

  * `path` : カスタムGeoRegionsのテンプレートリストがコピーされるパス。デフォルトは現在の作業ディレクトリ`pwd()`です。
  * `overwrite` : このフォルダにテンプレートファイルが存在する場合、上書きしますか？
