```
aggregate(method, object, scale; kw...)
```

`scale`を使用して`method`によって`Raster`、または`RasterStack`や`RasterSeries`内のすべての配列を集約します。

# 引数

  * `method`: 複数のセルの値を組み合わせて集約されたセルを生成できる`mean`や`sum`のような関数、または`Start()`や`Center()`のような[`Locus`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.locus)で、区間内のどこからサンプリングするかを指定します。
  * `object`: 集約するオブジェクト、例えば`AbstractRasterSeries`、`AbstractStack`、`AbstractRaster`または`Dimension`。
  * `scale`: 集約因子で、`Int`、各次元の`Int`の`Tuple`、または全次元を意味する`:`コロンで指定できます。通常`getindex`で使用できる任意の`Dimension`、`Selector`または`Int`の組み合わせも使用できます。キーが次元名の`Pair`または`NamedTuple`の`Tuple`も機能します。`Selector`を使用すると、インデックスの開始からの距離によってスケールが決まります。セレクタは最初のオフセットを見つけ、残りの部分に同じ集約サイズを繰り返します。

集約`scale`が配列の軸より大きい場合、軸の長さが使用されます。

# キーワード

  * `skipmissing`: `true`の場合、集約中に`missingval`はスキップされ、すべての欠損値の領域のみが`missingval(dst)`に集約されます。`false`の場合、1つ以上の`missingval`を含む集約領域には`missingval`が割り当てられます。デフォルトは`false`です。`skipmissing`の動作は関数`f`とは独立しており、完全に非欠損値にのみ適用されます。
  * `filename`: 直接書き込むためのファイル名、大きなファイルに便利です。
  * `suffix`: ファイル名に追加する文字列または値。`suffix`のタプルはスタックレイヤーに適用されます。`keys(stack)`がデフォルトです。
  * `progress`: 進捗バーを表示、デフォルトは`true`、`false`で非表示にします。
  * `threaded`: 操作を並行して実行、デフォルトは`false`です。場合によっては、`threaded`は単一スレッドの操作よりも大幅な速度向上をもたらすことがあります。これは、低解像度のラスターに書き込まれた複雑なジオメトリに対して真実である可能性がありますが、高解像度のラスターに対しては単純なジオメトリには当てはまらないかもしれません。非常に大きなラスターでは、スレッド処理が過剰なメモリ使用のために逆効果になることがあります。注意が必要です：`threaded`は、`BitArray`や競合条件が発生する可能性のある他の配列に書き込むインプレース関数では使用すべきではありません。
  * `vebose`: 潜在的な問題に関するメッセージを表示するかどうか。デフォルトは`true`です。

# 例

```jldoctest
using Rasters, RasterDataSources, Statistics, Plots
import ArchGDAL
using Rasters: Center
st = RasterStack(WorldClim{Climate}; month=1)
ag = aggregate(Center(), st, (Y(20), X(20)); skipmissingval=true, progress=false)
plot(ag)
savefig("build/aggregate_example.png"); nothing
# output

```

![aggregate](aggregate_example.png)

注: 現在、メモリバックされた配列で集約する方が速いです。必要に応じて`src`に対して[`read`](@ref)を使用してください。
