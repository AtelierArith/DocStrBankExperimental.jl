```
gamma = PolynomialStepSize(eta::AbstractFloat, [c::AbstractFloat=1.0]))
```

PolynomialStepSizeのコンストラクタ。

# 引数

  * `eta`: ステップサイズの指数で、(1/2,1]の範囲内である必要があります。
  * `c`: スケーリングファクター; デフォルトは`1.0`です。
