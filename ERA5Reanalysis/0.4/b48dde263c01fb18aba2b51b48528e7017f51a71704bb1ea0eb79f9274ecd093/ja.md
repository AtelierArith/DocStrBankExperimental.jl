```
getLandSea(
    e5ds :: ERA5Dataset,
    ereg :: ERA5Region = ERA5Region("GLB");
    save :: Bool = true,
    returnlsd :: Bool = true,
    smooth    :: Bool = false,
    σlon :: Int = 0,
    σlat :: Int = 0,
    iterations :: Int = 100,
    FT = Float64
) -> LandSea
```

指定された `ERA5Dataset` のために陸海マスクデータを取得します。

# 引数

  * `e5ds` : 指定された `ERA5Dataset` で、陸海データを `e5ds` に指定されたパスにダウンロードします。
  * `ereg` : 興味のあるERA5Regionで、各陸海データセットは指定された解像度によって異なります。

# キーワード引数

  * `save` : `true` の場合、将来の取得を容易にするために、e5ds.emaskで指定されたNetCDFファイルに陸海データセットのコピーを保存します（すなわち、ダウンロードを繰り返す必要がありません）。
  * `returnlsd` : `true` の場合、データを `LandSea` データセットとして返します。そうでない場合、データは単に e5ds.emask ディレクトリに保存されます。
  * `smooth` : `smooth` = true の場合、ImageFiltering.jl のガウシアンフィルターを使用して陸海マスクを平滑化でき、海岸線（すなわち、陸と海の境界）がぼやけます。
  * `σlon` : 経度方向で平滑化します（σlon の1の増加はおおよそ8ピクセルに相当します）。
  * `σlat` : 緯度方向で平滑化します（σlat の1の増加はおおよそ8ピクセルに相当します）。
  * `iterations` : ガウシアン平滑化の反復回数で、高いほど平滑化が半対数に近づきます。50-100回の反復が一般的には十分です。
