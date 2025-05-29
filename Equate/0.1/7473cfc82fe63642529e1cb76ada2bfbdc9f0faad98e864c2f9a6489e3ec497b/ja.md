```
テスト等価化のためのJuliaパッケージ。
```

主な機能：

*単一グループ（SG）* デザイン

  * `Linear` は線形等価化を提供します。
  * `Equipercentile` は等百分位数等価化を提供します。

*アンカーテストを用いた非同等グループ（NEAT）* デザイン

  * `Tucker`
  * `ChainedLinear`
  * `ChainedEquipercentile`
  * `BraunHolland`
  * `FrequencyEstimation`

など...

von Davier、Holland、Thayer（2004）によると、テスト等価化には5つの別々のステップがあります。

  * 最初のステップは、*前スムージング*。
  * 第二のステップは*スコア確率の推定*です。
  * 第三のステップは*連続化*です。
  * 第四のステップは*等価化*です。
  * 最後のステップは*等価化の標準誤差（SEE）の計算*です。
