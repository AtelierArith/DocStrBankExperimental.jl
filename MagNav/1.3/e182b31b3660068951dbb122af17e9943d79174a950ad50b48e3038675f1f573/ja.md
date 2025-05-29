```
map_chessboard!(map_map::Matrix, map_alt::Matrix, map_xx::Vector,
                map_yy::Vector, alt::Real;
                down_cont::Bool = true,
                dz              = 5,
                down_max        = 150,
                α               = 200)
```

`chessboard method`を実行し、地図を複数の高度に上方（および場合によっては下方）に続けて3Dマップを作成し、各水平グリッドポイントで垂直補間を行います。

参考文献: Cordell, Phillips, & Godson, U.S. Geological Survey Potential-Field Software Version 2.0, 1992.

**引数:**

  * `map_map`:   `ny` x `nx` 2Dグリッドターゲット（例：磁気）マップデータ [m] グリッド上
  * `map_alt`:   `ny` x `nx` 2Dグリッド高度マップデータ [m] [m] グリッド上
  * `map_xx`:    `nx` マップx方向（経度）座標 [m]
  * `map_yy`:    `ny` マップy方向（緯度）座標 [m]
  * `alt`:       上方継続後の最終マップ高度 [m]
  * `down_cont`: （オプション）必要に応じて下方継続する場合はtrue、`up_cont = true`の場合のみ使用
  * `dz`:        （オプション）上方継続ステップサイズ [m]
  * `down_max`:  （オプション）最大下方継続距離 [m]
  * `α`:         （オプション）下方継続の正則化パラメータ

**戻り値:**

  * `nothing`: `map_map`は上方継続されたマップデータで変異します
