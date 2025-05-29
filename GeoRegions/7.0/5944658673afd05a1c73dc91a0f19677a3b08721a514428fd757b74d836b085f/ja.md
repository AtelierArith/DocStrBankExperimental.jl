```
tableRectRegions(;
    path :: AbstractString = homedir(),
    custom :: Bool = true,
    giorgi :: Bool = false
) -> nothing
```

利用可能なすべてのRectRegionsを表形式で表示します。

# キーワード引数

  * `path` : カスタムRectRegionsのリストを取得するパス。デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `custom` : `true`の場合、ユーザー定義のカスタムRectRegionsを表示します。デフォルトは`true`です。
  * `giorgi` : `true`の場合、GFの事前定義されたRectRegionsを表示します。デフォルトは`true`です。
