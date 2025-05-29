```
map_chessboard(mapSd::MapSd, alt::Real;
               down_cont::Bool = true,
               dz              = 5,
               down_max        = 150,
               α               = 200)
```

`chessboard method`を実行し、地図を複数の高度に上方（および場合によっては下方）に続けて3Dマップを作成し、各水平グリッドポイントで垂直補間を行います。

参考文献: Cordell, Phillips, & Godson, U.S. Geological Survey Potential-Field Software Version 2.0, 1992.

**引数:**

  * `mapSd`:     `MapSd`スカラー磁気異常マップ構造体
  * `alt`:       上方継続後の最終マップ高度 [m]
  * `down_cont`: （オプション）必要に応じて下方継続する場合はtrue
  * `dz`:        （オプション）上方継続のステップサイズ [m]
  * `down_max`:  （オプション）最大下方継続距離 [m]
  * `α`:         （オプション）下方継続の正則化パラメータ

**戻り値:**

  * `mapS`: `MapS`スカラー磁気異常マップ構造体
