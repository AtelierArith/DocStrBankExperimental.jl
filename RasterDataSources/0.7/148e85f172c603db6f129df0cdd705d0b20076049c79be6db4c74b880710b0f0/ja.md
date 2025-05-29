```
getraster(T::Type{WorldClim{Elevation}}, [layer::Union{Tuple,Symbol}]; res::String="10m") => Union{Tuple,AbstractVector,String}
```

[`WorldClim`](@ref) [`Elevation`](@ref) データをダウンロードします。

# 引数

  * `layer`: `Symbol` または `(:elev,)` からの `Symbol` の `Tuple`。`layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `res`: ("30s", "2.5m", "5m", "10m") から選ばれた `String`、デフォルトは "10m" です。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
