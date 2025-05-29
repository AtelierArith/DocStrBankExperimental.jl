```
getraster(T::Type{WorldClim{Weather}}, [layer::Union{Tuple,Symbol}]; date) => Union{String,Tuple{String},Vector{String}}
```

[`WorldClim`](@ref) [`Weather`](@ref) データをダウンロードします。`layer`/s は `(:tmin, :tmax, :prec)` です。レイヤー引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `date`: `Date` または `DateTime` オブジェクト、日付の `Vector`、または開始/終了日付の `Tuple`。WorldClim Weather は日次のタイムステップで利用可能です。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
