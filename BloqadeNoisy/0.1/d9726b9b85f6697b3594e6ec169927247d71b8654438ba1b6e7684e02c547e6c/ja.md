```
function emulate
```

アンサンブルをエミュレートし、ビット列分布に対するアンサンブル平均を返します。

# 引数

  * `prob`: NoisySchrodingerProblem
  * `ntraj`: 軌道の数
  * `report_error`: サンプルから推定された2σを返します
  * `ensemble_algo`: どのタイプの並列化が望ましいか。EnsembleSimulationのドキュメントを参照してください
