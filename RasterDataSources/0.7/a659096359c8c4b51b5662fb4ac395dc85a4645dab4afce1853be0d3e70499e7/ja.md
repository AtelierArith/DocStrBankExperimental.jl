```
getraster(T::Type{WorldClim{Climate}}, [layer::Union{Tuple,Symbol}]; month, res::String="10m") => Vector{String}
```

[`WorldClim`](@ref) [`Climate`](@ref) データをダウンロードします。

# 引数

  * `layer` `Symbol` または `Symbol` の `Tuple` で、`(:tmin, :tmax, :tavg, :prec, :srad, :wind, :vapr)` から選択します。 `layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `month`: `Integer` または `Integer` の `AbstractArray`。 `1:12` から選択します。
  * `res`: ("30s", "2.5m", "5m", "10m") から選択する `String`、デフォルトは "10m" です。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
