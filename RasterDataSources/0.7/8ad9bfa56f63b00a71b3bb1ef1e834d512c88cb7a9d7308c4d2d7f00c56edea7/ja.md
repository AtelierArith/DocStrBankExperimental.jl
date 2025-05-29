```
getraster(source::Type{AWAP}, [layer]; date)
```

[`AWAP`](@ref) 気象データセットからデータをダウンロードします。 [www.csiro.au/awap](http://www.csiro.au/awap/) から取得できます。

AWAPデータセットにはASCII形式の`.grid`ファイルが含まれています。

# 引数

  * `layer` `Symbol`または`(:solar, :rainfall, :vprpress09, :vprpress15, :tmin, :tmax)`の`Symbol`の`Tuple`。`layer`引数がない場合、すべてのレイヤーがダウンロードされ、パスの`NamedTuple`が返されます。

# キーワード

  * `date`: `DateTime`、`AbstractVector`の`DateTime`、または開始日と終了日の`Tuple`。複数の日付の場合、複数のファイル名の`Vector`が返されます。AWAPは日次のタイムステップで利用可能です。

# 例

2001年の最初の月の降雨量をダウンロードします：

```julia
julia> getraster(AWAP, :rainfall; date=Date(2001, 1, 1):Day(1):Date(2001, 1, 31))

31-element Vector{String}:
 "/your/path/AWAP/rainfall/totals/20010101.grid"
 "/your/path/AWAP/rainfall/totals/20010102.grid"
 ...
 "/your/path/AWAP/rainfall/totals/20010131.grid"
```

ダウンロードされたファイルまたは既存のファイルのファイルパスが返されます。
