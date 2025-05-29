```
getraster(source::Type{EarthEnv{HabitatHeterogeneity}}, [layer]; res="25km")
```

[`EarthEnv`](@ref) 生息地の異質性データをダウンロードします。

# 引数

  * `layer`: `Symbol` または `(:cv, :evenness, :range, :shannon, :simpson, :std, :Contrast, :Correlation, :Dissimilarity, :Entropy, :Homogeneity, :Maximum, :Uniformity, :Variance)` の `Tuple`。 `layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `res`: `("1km", "5km", "25km")` から選ばれた `String`、デフォルトは "25km" です。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
