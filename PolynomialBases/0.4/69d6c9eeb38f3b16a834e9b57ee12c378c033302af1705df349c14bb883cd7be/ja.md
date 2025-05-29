```
utility_matrices(basis::NodalBasis{Line})
```

行列を返します

  * `D`, 導関数行列
  * `M`, 質量行列
  * `R`, 制限行列（境界への補間）
  * `B`, 境界法線行列
  * `MinvRtB = M \ R' * B`

フラックス再構成/修正手順の定式化に使用される、部分ごとの和演算子を用いた再構成による修正手順、Ranocha, Öffner, Sonar (2016) の「部分ごとの和演算子による再構成を介した修正手順」、Journal of Computational Physics 311, 299-328を参照してください。
