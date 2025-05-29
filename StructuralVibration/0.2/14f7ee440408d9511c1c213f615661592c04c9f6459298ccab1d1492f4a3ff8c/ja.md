```
StateSpaceFRFProblem(css::ContinuousStateSpace, freq, type, So, Se)
```

直接ソルバーにFRFを計算するためのデータを供給する構造体

**フィールド**

  * `css`: 連続時間状態空間モデル
  * `freq`: 興味のある周波数
  * `So`: 観測点の選択行列
  * `Se`: 励起点の選択行列

**注意** 出力方程式は y = So*x の形であると仮定されます。
