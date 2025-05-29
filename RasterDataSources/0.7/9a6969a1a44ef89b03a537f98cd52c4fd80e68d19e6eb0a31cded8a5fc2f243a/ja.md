```
getraster(T::Type{WorldClim{BioClim}}, [layer::Union{Tuple,AbstractVector,Integer}]; res::String="10m") => Union{Tuple,AbstractVector,String}
```

[`WorldClim`](@ref) [`BioClim`](@ref) データをダウンロードします。

# 引数

  * `layer`: `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)` の `Integer` またはタプル/範囲、または `(:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19)` の `Symbol`。`layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `res`: ("30s", "2.5m", "5m", "10m") から選ばれた `String`、デフォルトは "10m"。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
