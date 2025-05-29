```
readnl(geom, start_date = Date(2012, 04), end_date = Date(2023, 01))
```

特定のディレクトリから夜間光データを読み込み、放射とカバレッジを表す2つのラスターデータキューブを返します。この関数は、指定されたジオメトリに基づいてラスタをクロップします。

# 引数

  * `geom`: ラスタをクロップするために使用されるジオメトリオブジェクト。これは、シェープファイルからの`Geometry`、`Polygon`、`MultiPolygon`などのインスタンスである可能性があります。
  * `start_date`: データを読み込む期間の開始日（含む）。`Date`のインスタンスである必要があります。デフォルトは`Date(2012, 04)`です。
  * `end_date`: データを読み込む期間の終了日（含む）。`Date`のインスタンスである必要があります。デフォルトは`Date(2023, 01)`です。

# 戻り値

2つの`RasterDataCube`インスタンス。最初のものはクロップされた放射データを含み、2番目のものはクロップされたカバレッジデータを含みます。各`RasterDataCube`は、`start_date`から`end_date`までのデータを含み、昇順にソートされています。

# 例

```julia
using Shapefile
geom = Shapefile.Table("path_to_your_shapefile.shp").geometry[1]  # これを実際のシェープファイルに置き換えてください
start_date = Date(2015, 01)
end_date = Date(2020, 12)
rad_dc, cf_dc = readnl(geom, start_date, end_date)
```
