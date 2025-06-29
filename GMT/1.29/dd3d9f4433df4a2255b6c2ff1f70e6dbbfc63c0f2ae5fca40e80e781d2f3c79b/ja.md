```
Gdef = okada(G::GMTgrid; kw...)
```

### 引数

  * `G`: 変形が計算される領域とグリッド間隔を定義するグリッド。
  * `x_start`: 断層の開始点のx座標（断層面の左上隅）。
  * `y_start`: 断層の開始点のy座標。
  * `W`: 断層の幅（km）。
  * `L`: 断層の長さ（km）。
  * `depth`: 断層上部中心の深さ（km）（`depth` > 0）。
  * `strike`: 断層のトレース方向のストライク（北に対して0から360°）で、断層がトレースの右側に傾斜するように定義される。
  * `dip`: 断層の傾斜（断層面と水平面の間の角度、度）。
  * `rake`: 破裂中に吊り壁が動く方向で、断層のストライクに対して測定される（-180から180°）。
  * `slip`: `rake`方向の変位（`G`が地理座標の場合はkm、直交座標の場合は長さの単位）。
  * `open`: 引張成分における変位（`slip`と同じ単位）。
  * `nu`: ポアソン比、各方位に対して0.25がデフォルトの等方性媒体。
