```
BrooksCoreyRelativePermeabilities(
    sys_or_nph::Union{MultiPhaseSystem, Integer},
    exponents = 1.0,
    residuals = 0.0,
    endpoints = 1.0
)
```

ブロoks-Corey相対透過率関数のファミリーを実装する二次変数です。これは、限られた数のパラメータを持つ相対透過率のための単純な解析式です：

$$
K(S) = K_{max} * ((S - S_r)/(1 - S_r^{tot}))^N
$$

## フィールド

  * `exponents`: 各相の指数
  * `residuals`: 各相の残留飽和度
  * `endpoints`: 各相の最大相対透過率
  * `residual_total`: すべての相にわたる総残留飽和度
