```
arccircle(x0, y0, radius, start_angle, end_angle; z0=0, inc=2, gdataset=false)
```

### パラメータ

  * `x0`: 中心 X
  * `y0`: 中心 Y
  * `radius`: 円の半径。
  * `start_angle`: 弧の最初の点への角度（X正方向の時計回り）
  * `end_angle`: 弧の最後の点への角度（X正方向の時計回り）

### キーワード

  * `z0`: 中心 Z。オプションで、提供されない場合は出力は平面 2D になります
  * `inc`: 弧に沿った最大ステップ（度）。デフォルトは 2 度
  * `gdataset`: 入力が GMTdataset または Matrix の場合でも GDAL IGeometry を返します

### 戻り値

GMT データセットまたは GDAL IGeometry
