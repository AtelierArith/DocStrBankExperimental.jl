```
wmstest(wms::WMS; layer, size::Bool=false, kwargs...)
```

要求された解像度に基づいて、GetMapリクエスト文字列または結果の画像のサイズを生成するテスト関数です。これは、画像/グリッドを取得するコマンドを最初に生成することを目的としており、実行することはありません。特に、結果の画像サイズが巨大でないことを確認するのに便利です。

### パラメータ

  * `wms`: `wmsinfo`関数から取得したWMSタイプ。
  * `layer`: WMSサービスによって提供される関心のあるレイヤー番号またはレイヤー名。つまり、これらの形式の両方が許可されます: `layer=3` または `layer="Invented layer name"`
  * `size`: `false`の場合、GetMapリクエスト文字列を返し、そうでない場合は要求された解像度に基づく画像サイズを返します。

### `kwargs`は設定に使用されるキーワード/値のペアです

  * `region | limits`: 地域の制限。これは、`(xmin, xmax, ymin, ymax)`を定義する4つの要素を持つタプルまたは配列、またはGMTが認識できるすべての方法で制限を定義する文字列である可能性があります。レイヤーにデータが投影されている場合、地理座標での正方形の中心を設定する最初の2つの要素と、そのボックスの幅をメートル単位で指定する3番目の要素（`width`）を持つタプルまたは配列を使用できます。
  * `cellsize | pixelsize | resolution | res`: 要求されたセルサイズをメートル単位で設定します [デフォルト]。解像度が度で与えられる場合は、'd'を付加した文字列を使用します（例: `resolution="0.001d"`）。この方法は、レイヤーが地理座標系にある場合にのみ機能します。

### 戻り値

`size=false`の場合はGetMapリクエスト文字列、または結果の画像/グリッドサイズ `dim_x, dim_y` のいずれかです。

## 例

```
wmstest(wms, layer=34, region=(-8,39, 100000), pixelsize=100)

"WMS:http://tiles.maps.eox.at/?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetMap&LAYERS=s2cloudless-2020_3857&SRS=EPSG:900913&BBOX=-940555.9,4671671.6,-840555.9,4771671.68&FORMAT=image/jpeg&TILESIZE=256&OVERVIEWCOUNT=18&MINRESOLUTION=0.59716428347794&TILED=true"
```
