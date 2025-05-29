```
replace_missing(a::AbstractRaster, newmissingval)
replace_missing(a::AbstractRasterStack, newmissingval)
```

配列またはスタックの欠損値を新しい欠損値で置き換え、`missingval` フィールドも更新します。

# キーワード

  * `filename`: 大きなファイルに直接書き込むためのファイル名。
  * `suffix`: ファイル名に追加する文字列または値。`suffix` のタプルはスタックレイヤーに適用されます。`keys(stack)` がデフォルトです。

# 例

```jldoctest
using Rasters, RasterDataSources, ArchGDAL
A = Raster(WorldClim{Climate}, :prec; month=1) |> replace_missing
missingval(A)
# output
missing
```
