```
rmID(
    ID :: AbstractString;
    path :: AbstractString = geodir
) -> nothing
```

ID `ID` に関連付けられた GeoRegion を削除します。ID は正確でなければなりません。

# 引数

  * `ID` : GeoRegion を識別するために使用されるキーワード ID。           ID が無効な場合（つまり、使用されていない場合）、エラーが発生します。

# キーワード引数

  * `path` : カスタム GeoRegions のリストが取得されるパス。          デフォルトはホームディレクトリ `homedir()` です。
