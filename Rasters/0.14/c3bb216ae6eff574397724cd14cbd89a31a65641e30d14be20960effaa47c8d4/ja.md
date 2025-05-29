```
mosaic(f, regions...; kw...)
mosaic(f, regions; kw...)
```

`regions` の `Raster` または `RasterStack` を単一のオブジェクトに結合し、重複する領域を結合するために関数 `f` を使用します。

# 引数

  * `f`: `regions` が重複する値のための縮小関数。一般的な基本関数（`mean`, `sum`, `prod`, `first`, `last`, `minimum`, `maximum`, `length`）は最適化されており、多くのメモリまたはディスクベースのファイルで動作しますが、ユーザー定義の関数は、`op` がキーワードとして渡されない限り、大規模なスケールでは失敗する可能性があります。
  * `regions`: `Raster` または `RasterStack` の反復可能なオブジェクト。多くの領域がある場合、`Tuple` やスプラットを使用するよりも、`AbstractArray` を使用する方が通常は良いです。

# キーワード

  * `missingval`: 空の領域を埋め、最初の領域の `missingval` にデフォルト設定されます。
  * `op`: 縮小のための演算子、例えば `sum` のための `add_sum`。`sum` のような一般的なメソッドについては、これらは既知であり、自動的に検出されますが、他の関数については手動で提供することができ、大規模なスケールでも動作し続けます。
  * `atol`: インデックス値の比較のための絶対許容誤差。これは、浮動小数点エラーによる範囲値のわずかな違いのためにしばしば必要です。非浮動小数点次元には適用されません。許容誤差のタプルを渡すことができ、次元の順序に一致します。
  * `progress`: 進行状況バーを表示します。デフォルトは `true` で、`false` にすると非表示になります。
  * `read`: 書き込む前に遅延ラスタ領域を `read` します。これは、ソースと宛先のラスタ間にチャンクの整列の問題がある場合に役立つことがあります。デフォルトは `false` です。
  * `filename`: 直接書き込むためのファイル名。大きなファイルに便利です。
  * `suffix`: ファイル名に追加する文字列または値。`suffix` のタプルはスタックレイヤーに適用されます。`keys(stack)` がデフォルトです。
  * `force`: デフォルトは `false` です。`true` の場合、既に存在していてもファイルへの書き込みを強制的に行います。

モザイクに明らかな線のエラーがある場合は、`atol` の値を増やしてください。

# 例

ここでは、オーストラリアとアフリカをスタックから切り出し、`mosaic` で結合します。

```jldoctest
using Rasters, RasterDataSources, NaturalEarth, DataFrames, Dates, Plots
import ArchGDAL

countries = naturalearth("admin_0_countries", 110) |> DataFrame
climate = RasterStack(WorldClim{Climate}, (:tmin, :tmax, :prec, :wind); month=July)
country_climates = map(("Norway", "Denmark", "Sweden")) do name
    country = subset(countries, :NAME => ByRow(==(name)))
    trim(mask(climate; with=country); pad=10)
end
scandinavia_climate = trim(mosaic(first, country_climates; progress=false))
plot(scandinavia_climate)
savefig("build/mosaic_example_combined.png"); nothing

# output

```

### 国のモザイク

![mosaic](mosaic_example_combined.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHubの問題を報告してください。
