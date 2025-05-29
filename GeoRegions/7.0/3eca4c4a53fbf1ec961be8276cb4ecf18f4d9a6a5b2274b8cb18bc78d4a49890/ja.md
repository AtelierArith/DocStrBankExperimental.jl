```
isID(
    ID   :: AbstractString;
    path :: AbstractString = homedir(),
    throw   :: Bool = true,
    verbose :: Bool = false
) -> tf :: Bool
```

指定された `path` に定義されたカスタムリストに存在する GeoRegion が、ID `ID` であるかどうかを確認します。

# 引数

  * `ID` : GeoRegion を識別するために使用されるキーワード ID。       ID が無効な場合（つまり、使用されていない場合）、エラーがスローされます。

# キーワード引数

  * `path` : カスタム GeoRegions のリストが取得されるパス。          デフォルトは現在のディレクトリ `pwd()` です。
  * `throw` : `true` の場合、`ID` が有効な `GeoRegion` 識別子でないときに、Boolean `tf` を返すのではなくエラーをスローします。
  * `verbose` : 監視を容易にするための詳細なログ？ デフォルトは `false` です。

# 戻り値

  * `tf` : `true`/`false` のブール値。
