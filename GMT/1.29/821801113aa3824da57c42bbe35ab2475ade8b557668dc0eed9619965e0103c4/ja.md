```
circgeo(lon, lat; radius=X, proj="", s_srs="", epsg=0, dataset=false, unit=:m, np=120, shape="")
```

または

```
circgeo(lonlat; radius=X, proj="", s_srs="", epsg=0, dataset=false, unit=:m, np=120, shape="")
```

地理的または投影座標で地理的円（および他の形状）を計算します。

### 引数

  * `lonlat`:   - 経度、緯度（度）。Mx2行列の場合、行数と同じ数のセグメントを返します。               これを使用して異なる位置で複数の形状を計算します。この場合、出力タイプは               常にGMTdatasetsのベクトルです。

### キーワード引数

  * `radius`:   - メートル単位の円の半径（ただし`unit`を参照）または他の形状の外接円
  * `proj`または`s_srs`:  - 移動する楕円体の与えられた投影。proj4文字列またはWKTである可能性があります
  * `epsg`:     - 投影を指定する別の方法 [デフォルトはWGS84]
  * `dataset`:  - trueの場合、行列（単一の形状）ではなくGMTdatasetを返します
  * `unit`:     - `radius`がメートルでない場合、`unit=:km`、`unit=:Nautical`、または`unit=:Miles`のいずれかを使用します
  * `np`:       - 円が離散化されるポイントの数（デフォルト = 120）
  * `shape`:    - "triangle"、"square"、"pentagon"、または"hexagon"（または最初の文字）を持つオプションの文字列/シンボル               これらの幾何学のいずれかを円の代わりに計算します。この場合、`np`は無視されます。

### 戻り値

  * circ - 円の座標を持つMx2行列またはGMTdataset

### 例:

半径50 kmの(0,0)点の周りに円を計算します

```julia
    c = circgeo([0. 0], radius=50, unit=:k)
```
