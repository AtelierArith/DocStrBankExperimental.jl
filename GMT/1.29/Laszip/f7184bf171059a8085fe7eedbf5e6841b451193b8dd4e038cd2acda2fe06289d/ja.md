```
lazinfo(fname::AbstractString; veronly=false)
```

LASファイル`fname`に関する情報を表示します。そのファイルがグリッドである場合、通常のグリッドヘッダー情報を報告します。

  * `veronly`: trueの場合、laszipライブラリのバージョン番号のみを表示します。
