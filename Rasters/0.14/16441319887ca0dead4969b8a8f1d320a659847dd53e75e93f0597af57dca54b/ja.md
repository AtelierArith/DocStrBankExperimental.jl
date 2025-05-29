```
mask(A:AbstractRaster; with, missingval=missingval(A))
mask(x; with)
```

欠損値の `with` によってマスクされた `A` の値を持つ新しい配列を返します。`with` が幾何学的オブジェクトの場合は、`with` の形状によってマスクされます。

# 引数

  * `x`: `Raster` または `RasterStack`

# キーワード

  * `with`: `AbstractRaster`、または GeoInterface.jl 互換の任意のオブジェクトまたはテーブル。ポイントの座標参照系は `crs(A)` と一致する必要があります。
  * `invert`: マスクを反転させ、`with` に欠損がない領域をマスクし、`with` に欠損がある領域をマスクします。
  * `missingval`: 返されるファイルで使用する欠損値。
  * `filename`: 大きなファイルに便利な、直接書き込むためのファイル名。
  * `suffix`: ファイル名に追加する文字列または値。`suffix` のタプルはスタック層に適用されます。`keys(stack)` がデフォルトです。

# 幾何学キーワード

`with` が GeoInterface.jl 互換のオブジェクトである場合に使用できます：

  * `shape`: `data` を `:polygon`、`:line` または `:point` 幾何学として扱うことを強制します。ポイントやラインをポリゴンとして使用すると、予期しない結果が生じる可能性があります。
  * `boundary`: ポリゴンの場合、`:center` がポリゴン内にあるピクセル、ポリゴンがピクセルに `:touches` する場所、またはポリゴンの完全に `:inside` にあるピクセルを含めます。デフォルトは `:center` です。
  * `geometrycolumn`: `data` が Tables.jl 互換のテーブルである場合に幾何学が含まれる列を手動で選択するための `Symbol`、またはポイント座標の列のための `Symbol` のタプル。

# 例

マスクをリサンプリングすることによって、マスクされていない AWAP レイヤーをマスクされた WorldClim レイヤーでマスクします。

```julia
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates

# ファイルを読み込み、プロットする
awap = read(Raster(AWAP, :tmax; date=DateTime(2001, 1, 1)))
a = plot(awap; clims=(10, 45))

# worldclim ファイルをリサンプリングしてマスクを作成
wc = Raster(WorldClim{Climate}, :prec; month=1)
wc_mask = resample(wc; to=awap)

# マスク
awap_masked = mask(awap; with=wc_mask)
b = plot(awap_masked; clims=(10, 45))

savefig(a, "build/mask_example_before.png");
savefig(b, "build/mask_example_after.png"); nothing
# 出力

```

### `mask` 前：

### `mask` 後：

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで 100% 信頼できるわけではありません。問題が発生した場合は、github に問題を報告してください。
