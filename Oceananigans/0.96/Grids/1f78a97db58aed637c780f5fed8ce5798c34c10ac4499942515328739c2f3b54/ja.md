```
LatitudeLongitudeGrid(rectilinear_grid::RectilinearGrid; radius=R_Earth, origin=(0, 0))
```

`RectilinearGrid`から`LatitudeLongitudeGrid`を構築します。直交グリッドの水平座標は、球面地球の幾何学を考慮して、経度-緯度座標に度単位で変換されます。経度は、緯度の原点を用いておおよそ計算されます。

垂直座標とアーキテクチャは、入力グリッドから継承されます。

# キーワード引数

  * `radius`: 球の半径で、デフォルトは地球の平均半径（約 6371 km）
  * `origin`: 直交グリッドの原点を指定する度単位の（経度、緯度）のタプル
