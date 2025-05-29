```
rasterize([reducer], data; geometrycolumn, kw...)
```

GeoInterface.jl 互換のジオメトリまたはフィーチャ、または GeoInterface.jl オブジェクトの `:geometry` 列を持つ Tables.jl テーブル、または `geometrycolumn` で指定されたポイント列をラスタライズします。

# 引数

  * `reducer`: ピクセルをカバーまたは接触するすべてのジオメトリのフィル値を単一の値に減少させるための縮小関数。デフォルトは `last` です。反復可能なものを受け取り単一の値を返す任意の関数が機能します。カスタム関数も含まれます。ただし、`sum`、`first`、`last`、`minimum`、`maximum`、`extrema`、および `Statistics.mean` などの組み込みメソッドには最適化があります。これらは `count` よりも1桁以上速い場合があります。`count` は特別に処理されており、フィル値を必要としません。
  * `data`: GeoInterface.jl の `AbstractGeometry`、ネストされた `Vector` の `AbstractGeometry`、または `:geometry` 列またはポイントと値の列を含む Tables.jl 互換オブジェクト。この場合、`geometrycolumn` を指定する必要があります。

# キーワード

これらは可能な限り `data` から自動的に検出されます。

  * `fill`: ポリゴンを埋めるための値または値のセット。`Symbol` または `Symbol` のタプルがフィーチャからプロパティを取得するために使用されます。配列または他の反復可能なものが各ジオメトリに対して順番に使用されます。`fill` は現在の値の関数であることもできます。例: `x -> x + 1`。
  * `op`: 2つの値を受け取り1つを返す縮小関数。`min` から `minimum` など。一般的なメソッドには自動的に割り当てられますが、必須ではありません。ただし、通常は `reducer` の代わりに使用することができ、速くなることが多いです。
  * `to`: `Raster`、`RasterStack`、`Dimension` または `Extents.Extent` のタプル。`to` オブジェクトが提供されない場合、範囲はジオメトリから計算されます。さらに、`to` オブジェクトまたは `Extent` が `to` に渡されない場合、`size` または `res` キーワードも使用する必要があります。
  * `res`: 次元の解像度（通常はメートルまたは度）、`Real` または `Tuple{<:Real,<:Real}`。`to` が使用されない場合または `Extents.Extent` である場合、`size` が使用されない場合にのみ必要です。
  * `size`: 出力配列のサイズ、`Tuple{Int,Int}` または正方形のための単一の `Int`。`to` が使用されない場合または `Extents.Extent` である場合、`res` が使用されない場合にのみ必要です。
  * `crs`: `to` が渡されない場合または `Extent` である場合に結果のラスタに添付される `crs`。そうでない場合は `to` からの crs が使用されます。
  * `boundary`: ポリゴンの場合、`:center` がポリゴン内にあるピクセル、ポリゴンがピクセルに `:touches` する場合、またはポリゴンの完全に `:inside` であるピクセルを含めます。デフォルトは `:center` です。
  * `shape`: `data` を `:polygon`、`:line` または `:point` ジオメトリとして扱うよう強制します。ポイントやラインをポリゴンとして使用すると予期しない結果が生じる可能性があります。
  * `geometrycolumn`: `data` が Tables.jl 互換のテーブルである場合にジオメトリが含まれる列を手動で選択するための `Symbol`、またはポイント座標の列のための `Symbol` のタプル。
  * `progress`: 進行状況バーを表示します。デフォルトは `true`、`false` で非表示にします。
  * `vebose`: 潜在的な問題に関するメッセージを表示するかどうか。デフォルトは `true` です。
  * `threaded`: 操作を並行して実行します。デフォルトは `false`。特定の状況では、`threaded` は単一スレッドの操作よりも大幅な速度向上をもたらすことがあります。これは、低解像度のラスタに書き込まれた複雑なジオメトリに対して真である可能性がありますが、高解像度のラスタに対して単純なジオメトリには当てはまらないかもしれません。非常に大きなラスタでは、スレッド処理が過剰なメモリ使用のために逆効果になる可能性があります。また、注意が必要です。`threaded` は `BitArray` やレース条件が発生する可能性のある他の配列に書き込むインプレース関数では使用しないでください。
  * `threadsafe`: カスタム `reducer` および/または `op` 関数がスレッドセーフであることを指定します。すなわち、操作の順序やブロッキングは重要ではありません。たとえば、`sum` と `maximum` はスレッドセーフです。なぜなら、ネストされたブロックで実行した後、またはすべてのデータで実行した後の答えは（浮動小数点エラーを除いて）ほぼ同じだからです。対照的に、`median` や `last` はスレッドセーフではありません。なぜなら、ブロッキング（`median`）や順序（`last`）が重要だからです。
  * `filename`: 直接書き込むためのファイル名。大きなファイルに便利です。
  * `suffix`: ファイル名に追加する文字列または値。`suffix` のタプルはスタックレイヤーに適用されます。`keys(stack)` がデフォルトです。

スレッド処理に関する注意。`reducer`/`op` が `threadsafe` でない場合、`threaded=false` の方がパフォーマンスがはるかに良い場合があります。`sum`、`prod`、`maximum`、`minimum`、`count` および `mean`（`sum` と `count` を組み合わせることによって）はスレッドセーフです。アルゴリズムがスレッドセーフであることがわかっている場合は、すべての最適化を許可するために `threadsafe=true` を使用してください。`fill` に渡される関数は常にスレッドセーフであり、`threadsafe` 引数を無視します。

# 例

中国のシェープファイルをラスタライズし、境界を持つプロットを作成します。

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates, Shapefile, Downloads
using Rasters.Lookups

# 境界のシェープファイルをダウンロード
shapefile_url = "https://github.com/nvkelso/natural-earth-vector/raw/master/10m_cultural/ne_10m_admin_0_countries.shp"
shapefile_name = "country_borders.shp"
isfile(shapefile_name) || Downloads.download(shapefile_url, shapefile_name)

# 中国の形状を読み込む
china_border = Shapefile.Handle(shapefile_name).shapes[10]

# 境界ポリゴンをラスタライズ
china = rasterize(last, china_border; res=0.1, missingval=0, fill=1, boundary=:touches, progress=false)

# プロット
p = plot(china; color=:spring, legend=false)
plot!(p, china_border; fillalpha=0, linewidth=0.6)

savefig("build/china_rasterized.png"); nothing

# 出力

```

![rasterize](china_rasterized.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHub に問題を報告してください。
