```
tablePolyRegions(;
    path :: AbstractString = homedir(),
    custom :: Bool = true,
    srex :: Bool = false,
    ar6  :: Bool = false
) -> nothing
```

利用可能なすべてのPolyRegionsを表形式で表示します。

# キーワード引数

  * `path` : カスタムPolyRegionsのリストを取得するパス。デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `custom` : `true`の場合、カスタムユーザー定義のPolyRegionsを表示します。デフォルトは`true`です。
  * `srex` : `true`の場合、SREXの事前定義されたPolyRegionsを表示します。デフォルトは`true`です。
  * `ar6` : `true`の場合、IPCC AR6の事前定義されたPolyRegionsを表示します。デフォルトは`true`です。
