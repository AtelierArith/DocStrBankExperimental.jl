```
resample(x; kw...)
resample(xs...; to=first(xs), kw...)
```

`resample`は`warp`（GDALの`gdalwarp`を使用）を利用して、[`Raster`](@ref)または[`RasterStack`](@ref)を新しい`resolution`に再サンプリングし、オプションで新しい`crs`に変更するか、オブジェクト`to`の境界、解像度、crsにスナップします。

`AbstractProjected`ルックアップのない次元（`Ti`次元など）は、GDALを使用して反復的に再サンプリングされ、単一の配列に結合されます。

各軸ごとに投影を独立して変換できる場合、[`reproject`](@ref)を使用する方が高速で正確な場合があります。

このメソッドを利用可能にするには、`using ArchGDAL`を実行してください。

# 引数

  * `x`: 再サンプリングするオブジェクト。

# キーワード

  * `to`: `Raster`、`RasterStack`、`Dimension`の`Tuple`または`Extents.Extent`。`to`オブジェクトが提供されない場合、範囲は`x`から計算されます。
  * `res`: 次元の解像度（通常はメートルまたは度）、`Real`または`Tuple{<:Real,<:Real}`。`to`が使用されない場合または`Extents.Extent`であり、`size`が使用されない場合にのみ必要です。
  * `size`: 出力配列のサイズ、`Tuple{Int,Int}`または正方形のための単一の`Int`。`to`が使用されない場合または`Extents.Extent`であり、`res`が使用されない場合にのみ必要です。
  * `crs`: `to`が渡されない場合または`Extent`である場合に結果のラスタに添付される`crs`。それ以外の場合は、`to`からのcrsが使用されます。
  * `method`: 再サンプリングに使用するメソッドを指定する`Symbol`または`String`。[`gdalwarp`](https://gdal.org/programs/gdalwarp.html#cmdoption-gdalwarp-r)のドキュメントから：

      * `:near`: 最近傍再サンプリング（デフォルト、最速のアルゴリズム、最悪の補間品質）。
      * `:bilinear`: バイリニア再サンプリング。
      * `:cubic`: キュービック再サンプリング。
      * `:cubicspline`: キュービックスプライン再サンプリング。
      * `:lanczos`: ランツォスウィンドウ付きシンク再サンプリング。
      * `:average`: 平均再サンプリング、すべての非NODATA寄与ピクセルの加重平均を計算します。すべての非NODATA寄与ピクセルのrms二乗平均/二次平均（GDAL >= 3.3）
      * `:mode`: モード再サンプリング、サンプリングされたポイントの中で最も頻繁に現れる値を選択します。
      * `:max`: 最大再サンプリング、すべての非NODATA寄与ピクセルから最大値を選択します。
      * `:min`: 最小再サンプリング、すべての非NODATA寄与ピクセルから最小値を選択します。
      * `:med`: 中央再サンプリング、すべての非NODATA寄与ピクセルの中央値を選択します。
      * `:q1`: 第一四分位再サンプリング、すべての非NODATA寄与ピクセルの第一四分位値を選択します。
      * `:q3`: 第三四分位再サンプリング、すべての非NODATA寄与ピクセルの第三四分位値を選択します。
      * `:sum`: すべての非NODATA寄与ピクセルの加重合計を計算します（GDAL 3.1以降）。

    NODATA値は`missingval`に設定されます。
  * `filename`: 直接書き込むためのファイル名、大きなファイルに便利です。
  * `suffix`: ファイル名に追加する文字列または値。`suffix`のタプルはスタックレイヤーに適用されます。`keys(stack)`がデフォルトです。

注意：

  * GDALは、`crs`のタイプを`EPSG`から`WellKnownText`に変更するなど、ラスタに予期しない変更を引き起こす可能性があります（同じCRSを表します）。

# 例

WorldClimレイヤーをEarthEnvレイヤーに合わせて再サンプリングします：

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots
A = Raster(WorldClim{Climate}, :prec; month=1)
B = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)

a = plot(A)
b = plot(resample(A; to=B))

savefig(a, "build/resample_example_before.png");
savefig(b, "build/resample_example_after.png"); nothing

# output
```

### `resample`の前：

![before resample](resample_example_before.png)

### `resample`の後：

![after resample](resample_example_after.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHubの問題を報告してください。
