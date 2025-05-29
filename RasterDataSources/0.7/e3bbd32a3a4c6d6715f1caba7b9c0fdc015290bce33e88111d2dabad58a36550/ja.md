```
getraster(source::Type{CHELSA{BioClim}}, [layer]; version = 2, [patch]) => Union{Tuple,String}
```

[`CHELSA`](@ref) [`BioClim`](@ref) データを [chelsa-climate.org](https://chelsa-climate.org/) からダウンロードします。

# 引数

  * `layer`: `Integer` または `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)` の整数のタプル/範囲、または `(:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19)` のシンボル。`layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード引数

  * `version`: 現在の CHELSA バージョンを示す `Integer`、現在は `1` または `2` のいずれか。
  * `patch`: CHELSA パッチ番号を示す `Integer`。最新のパッチ (V1.2 および V2.1) がデフォルトです。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
