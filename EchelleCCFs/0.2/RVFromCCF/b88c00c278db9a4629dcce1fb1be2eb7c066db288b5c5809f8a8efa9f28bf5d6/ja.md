```
`measure_rv_from_ccf(vels, ccf, [ccf_var]; alg )`
```

指定されたアルゴリズムオブジェクトを使用してCCFに基づいて推定RVを返します。入力：

  * `vels`: CCFが評価された速度の配列。
  * `ccf`: CCFの値の配列

オプションの引数：

  * `alg`: CCFからRVとその不確実性を測定する方法を指定するファンクタ。オプションには次が含まれます：

MeasureRvFromCCFGaussian（デフォルト）、MeasureRvFromCCFQuadratic、MeasureRvFromCCFCentroid、およびMeasureRvFromMinCCF。
