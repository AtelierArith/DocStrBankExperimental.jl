```
mask!(x; with, missingval=missingval(A))
```

`with`の欠損値によって`A`をマスクするか、`with`がポリゴンである場合は`with`の外側のすべての値によってマスクします。

`with`がポリゴンである場合、ポリゴンの外側にある点が`missingval(A)`で置き換えられた新しい配列を作成します。

`with`の欠損値によってマスクされた`A`の値、またはポリゴンによってマスクされた新しい配列を返します。

# 引数

  * `x`: `Raster`または`RasterStack`。

# キーワード

  * `with`: 別の`AbstractRaster`、`Tuple`ポイントの`AbstractVector`、または任意のGeoInterface.jl `AbstractGeometry`。ポイントの座標参照系は`crs(A)`と一致する必要があります。
  * `invert`: マスクを反転させ、`with`に欠損がない領域をマスクし、`with`に欠損がある領域をマスクします。
  * `missingval`: マスクされた領域の`A`に書き込む欠損値。デフォルトは`missingval(A)`です。

# 例

マスクされたWorldClimレイヤーでマスクされていないAWAPレイヤーをマスクするために、まずマスクをサイズと投影に合わせて再サンプリングします。

```julia
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates

# ファイルを読み込み、プロットする
awap = read(RasterStack(AWAP, (:tmin, :tmax); date=DateTime(2001, 1, 1)))
a = plot(awap; clims=(10, 45), c=:imola)

# worldclimファイルを再サンプリングしてマスクを作成
wc = Raster(WorldClim{Climate}, :prec; month=1)
wc_mask = resample(wc; to=awap)

# マスク
mask!(awap; with=wc_mask)
b = plot(awap; clims=(10, 45))

savefig(a, "build/mask_bang_example_before.png");
savefig(b, "build/mask_bang_example_after.png"); nothing

# 出力

```

### `mask!`の前:

### `mask!`の後:

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
