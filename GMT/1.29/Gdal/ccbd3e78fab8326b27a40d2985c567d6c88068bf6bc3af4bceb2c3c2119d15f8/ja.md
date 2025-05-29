```
arcellipse(x0, y0, primary_radius, secondary_radius, start_angle, end_angle; rotation=0, z0=0, inc=2, gdataset=false)
```

### パラメータ

  * `x0`: 中心 X
  * `y0`: 中心 Y
  * `primary_radius`: 楕円の X 半径。
  * `secondary_radius`: 楕円の Y 半径。
  * `start_angle`: 弧の最初の点への角度（X 正方向の時計回り）
  * `end_angle`: 弧の最後の点への角度（X 正方向の時計回り）

### キーワード

  * `rotation`: 楕円の時計回りの回転。
  * `z0`: 中心 Z。オプションで、提供されない場合は出力は平面 2D になります。
  * `inc`: 弧に沿った最大ステップ（度）。デフォルトは 2 度です。
  * `gdataset`: 入力が GMTdataset または行列であっても GDAL IGeometry を返します。

### 返り値

GMT データセットまたは GDAL IGeometry
