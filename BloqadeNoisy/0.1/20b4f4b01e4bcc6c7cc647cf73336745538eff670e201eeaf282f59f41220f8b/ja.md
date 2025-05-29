```
function emulate
```

アンサンブルをエミュレートし、一連の期待値のアンサンブル平均を返します

# 引数

  * `prob`: NoisySchrodingerProblem
  * `ntraj`: 軌道の数
  * `expectations`: 観測量を表すエルミート演算子のセット。行列のようなオブジェクト
  * `shots`: 固定されたショット数で解を再サンプリングするかどうか。`shots = 0` の場合は再サンプリングしません
  * `report_error`: サンプルから推定された2σを返します。期待値が計算基底で対角である必要があります
  * `ensemble_algo`: どのタイプの並列化が望ましいか。EnsembleSimulationのドキュメントを参照してください
