```
rasterize!([reducer], dest, data; kw...)
```

`data`内のジオメトリを[`Raster`](@ref)または[`RasterStack`](@ref) `dest`にラスタライズし、`fill`で指定された値を使用します。

# 引数

  * `dest`: ラスタライズするための`Raster`または`RasterStack`。
  * `reducer`: ピクセルをカバーまたは接触するすべてのジオメトリのフィル値を単一の値に減少させるための縮小関数。デフォルトは`last`です。イテラブルを受け取り単一の値を返す任意の関数が機能しますが、`sum`、`first`、`last`、`minimum`、`maximum`、`extrema`および`Statistics.mean`などの組み込みメソッドには最適化があります。これらは`count`よりも1桁以上速い場合があります。`count`は特別に処理され、フィル値を必要としません。
  * `data`: GeoInterface.jlの`AbstractGeometry`、ネストされた`Vector`の`AbstractGeometry`、または`:geometry`列またはポイントと値の列を含むTables.jl互換オブジェクト。この場合、`geometrycolumn`を指定する必要があります。

# キーワード

これらは可能な限り`A`と`data`から自動的に検出されます。

  * `fill`: ポリゴンを埋めるための値または値の配列。`Symbol`または`Symbol`のタプルは、フィーチャからプロパティを取得するために使用されます。配列または他のイテラブルは、各ジオメトリに対して順番に使用されます。`fill`は現在の値の関数であることもできます。例: `x -> x + 1`。
  * `op`: 2つの値を受け取り1つを返す縮小関数。`min`から`minimum`のように。一般的なメソッドには自動的に割り当てられますが、必須ではありません。しかし、通常は`reducer`の代わりに使用することができ、速くなることが多いです。
  * `to`: `Raster`、`RasterStack`、`Dimension`の`Tuple`または`Extents.Extent`。`to`オブジェクトが提供されない場合、範囲はジオメトリから計算されます。さらに、`to`オブジェクトまたは`Extent`が`to`に渡されない場合、`size`または`res`キーワードも使用する必要があります。
  * `res`: 次元の解像度（通常はメートルまたは度）、`Real`または`Tuple{<:Real,<:Real}`。`to`が使用されない場合または`Extents.Extent`であり、`size`が使用されない場合にのみ必要です。
  * `size`: 出力配列のサイズ、`Tuple{Int,Int}`または正方形の単一の`Int`として。`to`が使用されない場合または`Extents.Extent`であり、`res`が使用されない場合にのみ必要です。
  * `crs`: `to`が渡されない場合または`Extent`である場合に結果のラスタに添付される`crs`。そうでない場合は`to`からのcrsが使用されます。
  * `boundary`: ポリゴンの場合、`:center`がポリゴン内にあるピクセル、ポリゴンがピクセルに`touches`する場所、またはポリゴンの完全に`inside`であるピクセルを含めます。デフォルトは`:center`です。
  * `shape`: `data`を`:polygon`、`:line`または`:point`ジオメトリとして扱うよう強制します。ポイントやラインをポリゴンとして使用すると、予期しない結果が生じる可能性があります。
  * `geometrycolumn`: `data`がTables.jl互換のテーブルである場合にジオメトリが含まれている列を手動で選択するための`Symbol`、またはポイント座標の列のための`Symbol`のタプル。
  * `progress`: 進行状況バーを表示します。デフォルトは`true`、`false`で非表示にします。
  * `vebose`: 潜在的な問題に関するメッセージを表示するかどうか。デフォルトは`true`です。
  * `threaded`: 操作を並行して実行します。デフォルトは`false`です。特定の状況では、`threaded`は単一スレッドの操作よりも大幅な速度向上をもたらすことがあります。これは、低解像度のラスタに書き込まれた複雑なジオメトリに当てはまる場合がありますが、高解像度のラスタに対して単純なジオメトリには当てはまらないかもしれません。非常に大きなラスタでは、スレッド処理が過剰なメモリ使用のために逆効果になることがあります。また、注意が必要です：`threaded`は、競合状態が発生する可能性のある`BitArray`や他の配列に書き込むインプレース関数では使用すべきではありません。
  * `threadsafe`: カスタム`reducer`および/または`op`関数がスレッドセーフであることを指定します。すなわち、操作の順序やブロッキングが重要でないことを意味します。例えば、`sum`や`maximum`はスレッドセーフです。なぜなら、ネストされたブロックで実行した後、またはすべてのデータで実行した後の答えは（浮動小数点エラーを除いて）ほぼ同じだからです。対照的に、`median`や`last`はスレッドセーフではありません。なぜなら、ブロッキング（`median`）や順序（`last`）が重要だからです。
  * `to`: `Raster`、`RasterStack`、`Dimension`の`Tuple`または`Extents.Extent`。`to`オブジェクトが提供されない場合、範囲はジオメトリから計算されます。さらに、`to`オブジェクトまたは`Extent`が`to`に渡されない場合、`size`または`res`キーワードも使用する必要があります。
  * `res`: 次元の解像度（通常はメートルまたは度）、`Real`または`Tuple{<:Real,<:Real}`。`to`が使用されない場合または`Extents.Extent`であり、`size`が使用されない場合にのみ必要です。
  * `size`: 出力配列のサイズ、`Tuple{Int,Int}`または正方形の単一の`Int`として。`to`が使用されない場合または`Extents.Extent`であり、`res`が使用されない場合にのみ必要です。
  * `crs`: `to`が渡されない場合または`Extent`である場合に結果のラスタに添付される`crs`。そうでない場合は`to`からのcrsが使用されます。
  * `boundary`: ポリゴンの場合、`:center`がポリゴン内にあるピクセル、ポリゴンがピクセルに`touches`する場所、またはポリゴンの完全に`inside`であるピクセルを含めます。デフォルトは`:center`です。
  * `shape`: `data`を`:polygon`、`:line`または`:point`ジオメトリとして扱うよう強制します。ポイントやラインをポリゴンとして使用すると、予期しない結果が生じる可能性があります。

# 例

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates, Shapefile, GeoInterface, Downloads
using Rasters.Lookups

# 国境のシェープファイルをダウンロード
shapefile_url = "https://github.com/nvkelso/natural-earth-vector/raw/master/10m_cultural/ne_10m_admin_0_countries.shp"
shapefile_name = "country_borders.shp"
isfile(shapefile_name) || Downloads.download(shapefile_url, shapefile_name)

# インドネシアの形状を読み込む
indonesia_border = Shapefile.Handle(shapefile_name).shapes[1]

# インドネシアの領域の空のEPSG 4326投影ラスタを作成
dimz = X(Projected(90.0:0.1:145; sampling=Intervals(), crs=EPSG(4326))),
       Y(Projected(-15.0:0.1:10.9; sampling=Intervals(), crs=EPSG(4326)))

A = zeros(UInt32, dimz; missingval=UInt32(0))

# 各インドネシアの島を異なる番号でラスタライズします。島は
# マルチポリゴンのリングであるため、`GI.getring`を使用してすべてを個別に取得します。
islands = collect(GeoInterface.getring(indonesia_border))
rasterize!(last, A, islands; fill=1:length(islands), progress=false)

# そしてプロット
p = plot(Rasters.trim(A); color=:spring)
plot!(p, indonesia_border; fillalpha=0, linewidth=0.7)

savefig("build/indonesia_rasterized.png"); nothing

# 出力

```

![rasterize](indonesia_rasterized.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHubの問題を報告してください。
