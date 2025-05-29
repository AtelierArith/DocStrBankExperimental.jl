```
extract(x, geometries; kw...)
```

指定されたジオメトリのために `Raster` または `RasterStack` の値を抽出し、`:geometry` と `Raster` または `RasterStack` レイヤーの値のプロパティを持つ `Vector{NamedTuple}` を返します。

ライン、ラインストリング、およびリニアリングの場合、ラインが触れる各ピクセルのポイントが抽出されます。

ポリゴンの場合、ポリゴンによってカバーされる中心を持つすべてのセルが返されます。

オブジェクトがポイントタプルの長さよりも多くの次元を持つ場合、単一の値の代わりにスライスされた配列またはスタックが返されることに注意してください。

# 引数

  * `x`: 値を抽出するための `Raster` または `RasterStack`。
  * `data`: GeoInterface.jl の `AbstractGeometry`、ネストされた `Vector` の `AbstractGeometry`、または `:geometry` 列またはポイントと値の列を含む Tables.jl 互換オブジェクト。この場合、`geometrycolumn` を指定する必要があります。

# キーワード

  * `geometry`: 行に `:geometry` フィールドを含め、これはタプルポイントになります。ポイントの場合は元のポイント、ラインおよびポリゴン抽出の場合はピクセル中心点になります。デフォルトは `true`。
  * `index`: 行に抽出されたポイントの `:index` フィールドを含める。デフォルトは `false`。
  * `name`: 抽出する `RasterStack` のレイヤーに対応する `Symbol` または `Tuple` の `Symbol`。デフォルトではすべてのレイヤーが抽出されます。
  * `skipmissing`: 欠損ポイントを自動的にスキップします。
  * `flatten`: 複数のジオメトリから抽出されたポイントを単一のベクターにフラット化します。デフォルトは `true`。混合されていないポイントジオメトリは常にフラット化されます。フラット化は遅く、シングルスレッドであるため、`flatten=false` は `threaded=true` と組み合わせることで大きなパフォーマンス向上をもたらす可能性があります。
  * `atol`: `Lookup` に `Points` が含まれる場合の浮動小数点ルックアップ値の許容誤差。`atol` は `Intervals` には無視されます。
  * `boundary`: ポリゴンの場合、`:center` がポリゴン内にあるピクセル、ポリゴンがピクセルに `:touches` する場所、またはポリゴンの完全に `:inside` にあるピクセルを含めます。デフォルトは `:center`。
  * `geometrycolumn`: `data` が Tables.jl 互換のテーブルである場合にジオメトリが含まれている列を手動で選択するための `Symbol`、またはポイント座標の列のための `Symbol` のタプル。

# 例

ここでは、マウンテンピグミーポッサム、*Burramis parvus* の発生に一致するポイントを抽出します。これは種分布モデルを適合させるために使用できます。

```julia
using Rasters, RasterDataSources, ArchGDAL, GBIF2, CSV

# BioClim レイヤーのスタックを取得し、欠損値を `missing` で置き換えます
st = RasterStack(WorldClim{BioClim}, (1, 3, 5, 7, 12)) |> replace_missing

# 一部の発生データをダウンロードします
obs = GBIF2.occurrence_search("Burramys parvus"; limit=5, year="2009")

# `extract` を使用して各観測ポイントでのすべてのレイヤーの値を取得します。
# 遅延イテレータから `Vector` を取得するために `collect` を使用します。
extract(st, obs; skipmissing=true)

# 出力
5-element Vector{NamedTuple{(:geometry, :bio1, :bio3, :bio5, :bio7, :bio12)}}:
 (geometry = (0.21, 40.07), bio1 = 17.077084f0, bio3 = 41.20417f0, bio5 = 30.1f0, bio7 = 24.775f0, bio12 = 446.0f0)
 (geometry = (0.03, 39.97), bio1 = 17.076923f0, bio3 = 39.7983f0, bio5 = 29.638462f0, bio7 = 24.153847f0, bio12 = 441.0f0)
 (geometry = (0.03, 39.97), bio1 = 17.076923f0, bio3 = 39.7983f0, bio5 = 29.638462f0, bio7 = 24.153847f0, bio12 = 441.0f0)
 (geometry = (0.52, 40.37), bio1 = missing, bio3 = missing, bio5 = missing, bio7 = missing, bio12 = missing)
 (geometry = (0.32, 40.24), bio1 = 16.321388f0, bio3 = 41.659454f0, bio5 = 30.029825f0, bio7 = 25.544561f0, bio12 = 480.0f0)
```

注意: ポイントと他のジオメトリが混在する配列、ジオメトリコレクション、またはフィーチャコレクションを渡すと、未定義の結果が得られます。 ```
