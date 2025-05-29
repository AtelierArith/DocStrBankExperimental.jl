```
GI[,coast] = worldrectangular(GI; proj::String="+proj=vandg", pm=0, latlim=:auto, coast=false)
```

さまざまな投影法を用いて、長方形の地図を作成してみてください。

  * `GI`: GMTgrid または GMTimage データ型。`GI` はグリッドまたは画像のファイル名を持つ文字列でも構いません。
  * `proj`: 投影を説明する PROJ4 文字列。
  * `pm`: 投影の本初子午線（デフォルトは 0）。
  * `latlim または latlims`: 長方形の地図がトリミングされる緯度。デフォルト（:auto）は、完全に埋められたグリッド/画像を得るためにトリミングを試みることを意味します。`latlim=(lat_s,lat_n)` または `latlim=lat` を使用すると、`latlim=(-lat,lat)` と同等になります。
  * `coast`: `proj` で投影された海岸線も返します。`coast=res` を渡すと、`res` は GMT 海岸線解像度のいずれか（*例* :crude, :low, :intermediate）になります。`coast=true` は <==> `coast=:crude` です。`coast=D` を渡すと、`D` は GSHHG GMT データベース以外の出所を持つ海岸線ポリゴンを含む GMTdataset のベクトルになります。

### 戻り値

グリッドまたは画像、オプションで海岸線...またはエラー。多くの投影法は、この関数で実装された手順をサポートしていません。動作するかどうかは、PROJ の `+over` オプションによって制御されます https://proj.org/usage/projections.html#longitude-wrapping

### 例:

G = worldrectangular("@earth*relief*10m_g")    imshow(G)
