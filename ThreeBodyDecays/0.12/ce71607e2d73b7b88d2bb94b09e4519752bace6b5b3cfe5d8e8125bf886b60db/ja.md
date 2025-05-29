```
amplitude(dc::DecayChain, orientation_angles::PlaneOrientation, σs::MandelstamTuple; kw...)
```

与えられた崩壊系列の振幅を計算し、最終状態の回転に適用される方向角を考慮します。

# 引数

  * `dc::DecayChain`: システムの構成（例：スピン、パリティなど）を含む崩壊系列オブジェクト。
  * `orientation_angles::PlaneOrientation`: 最終状態の平面方向角（`α`、`cosβ`、`γ`）を表す名前付きタプル。
  * `σs::MandelstamTuple`: プロセスの運動量不変量を記述するマンデルスタム変数を表すタプル。
  * `kw...`: 基本的な`amplitude`計算に渡される追加のキーワード引数（例：`refζs`参照運動量）。

# 戻り値

  * 四次元の振幅配列

# 詳細

この関数はまず整列した振幅の配列を計算します。次に、それをウィグナーD行列と収束させます。
