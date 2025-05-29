```
ds = TIFFDataset(fname::AbstractString,mode = "r"; varname = "band",
                 projection = "EPSG:4326",
                 catbands = false,
                 dimnames = ("cols","rows","bands"))
```

GeoTIFFファイル名`fname`からデータセット構造を作成します。[ArchGDAL](https://github.com/yeesian/ArchGDAL.jl)を使用します。データ変数は`varname`（バンド番号に続く）と呼ばれます。データセット`ds`には、投影座標（GeoTIFFファイルで定義された通り）を表す仮想変数`x`、`y`および対応する経度/緯度（`projection`パラメータで定義された投影を使用）が含まれます。次元の名前は`dimnames`パラメータを使用して適応できます。投影の種類は、仮想変数`crs`の属性（`grid_mapping_name`、`longitude_of_central_meridian`、`false_easting`、`false_northing`、`latitude_of_projection_origin`、`scale_factor_at_central_meridian`、`longitude_of_prime_meridian`、`semi_major_axis`、`inverse_flattening`、... 使用される投影に応じて）を確認することで確認できます。属性`crs_wkt`は、座標参照系をいわゆる["Well-Known Text"](https://en.wikipedia.org/wiki/Well-known_text_representation_of_coordinate_reference_systems)として説明します。

CF規約に加えて、インデックスと投影座標の間の線形マッピングを説明する6つの数値を持つ属性`GeoTransform` [1] もあります。点`(i,j)`の投影座標は次のように計算されます：

```julia
shift = 0.5 # center
x_geo = GeoTransform[1] + (i-shift) * GeoTransform[2] + (j-shift) * GeoTransform[3]
y_geo = GeoTransform[4] + (i-shift) * GeoTransform[5] + (j-shift) * GeoTransform[6]
```

`catbands`をtrueに設定すると、すべてのバンドが`varname`という単一の変数に連結されます。`catbands`がtrueの場合、すべてのバンドが同じノーデータ値、オフセット、スケールファクターを持っていることを確認するのはユーザーの責任です。コマンドラインツール`gdalinfo filename`を使用するか、ArchGDALを使用してファイルを検査してください。これが当てはまらない場合は、`catbands = true`を使用すべきではありません。

例：

```julia
using TIFFDatasets
fname = download("https://data-assimilation.net/upload/Alex/TIFF/S2_1-12-19_48MYU_0.tif")
ds = TIFFDataset(fname)
band1 = ds["band1"][:,:];
longitude = ds["lon"][:,:];
latitude = ds["lat"][:,:];
# x,y ネイティブ投影
x = ds["x"][:,:];
y = ds["y"][:,:];
# 座標参照系を"Well-Known Text"として
crs_wkt = ds["crs"].attrib["crs_wkt"];
```

パフォーマンスの理由から、大量の個々の要素を読み込むこと（または`sum`、`mean`などの関数を使用すること）を避け、むしろ全体の配列を読み込むべきです。例えば：

```
julia> @time sum(ds["band1"]) # 遅い
  0.062227秒 (721.65 k アロケーション: 22.045 MiB)
6403.1743f0

julia> @time sum(ds["band1"][:,:]) # はるかに速い
  0.000381秒 (765 アロケーション: 302.781 KiB)
6403.5527f0
```

データセットは、[CommonDataModel.jl](https://github.com/JuliaGeo/CommonDataModel.jl)の関数を使用して操作できます。ファイルへの書き込みは現在サポートされていません（プルリクエストは歓迎します！）。

参考文献：

  * [1] [GDAL GeoTransform](https://gdal.org/tutorials/geotransforms_tut.html#transformation-from-image-coordinate-space-to-georeferenced-coordinate-space)
