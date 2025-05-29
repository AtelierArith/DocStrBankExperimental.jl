```
extend(xs...; [to])
extend(xs; [to])
extend(x::Union{AbstractRaster,AbstractRasterStack}; to, kw...)
```

複数の [`AbstractRaster`](@ref) を拡張して、すべての `xs` がカバーする領域、またはキーワード引数 `to` に一致させます。

# キーワード

  * `to`: 拡張するラスタまたは次元。`to` キーワードが渡されない場合、すべての `xs` の最大共有領域が使用されます。
  * `touches`: `true` または `false`。オブジェクトの範囲に `Touches` ラッパーを使用するかどうか。例えば、ゾーン統計にラインを含める必要がある場合は、`true` を使用するべきです。
  * `filename`: 直接書き込むためのファイル名。大きなファイルに便利です。
  * `suffix`: ファイル名に追加する文字列または値。`suffix` のタプルはスタックレイヤーに適用されます。`keys(stack)` がデフォルトです。

```jldoctest
using Rasters, RasterDataSources, Plots
evenness = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)
rnge = Raster(EarthEnv{HabitatHeterogeneity}, :range)

# 南アメリカを大まかに切り取る
sa_bounds = X(-88 .. -32), Y(-57 .. 13)
sa_evenness = evenness[sa_bounds...]

# 世界全体のラスタに一致させるために範囲を拡張する
sa_range = extend(sa_evenness; to=rnge)
plot(sa_range)

savefig("build/extend_example.png");
nothing
# output
```

![extend](extend_example.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
