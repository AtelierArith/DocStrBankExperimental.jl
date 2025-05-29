```
Interpolation <: AbstractOptimizationLayer
```

ブラックボックス最適化器の区分線形補間。

# フィールド

  * `maximizer`: 基本となるargmax関数
  * `λ::Float64`: スムージングパラメータ（小さいほどより忠実な近似、大きいほどより情報的な勾配）

参考文献: [https://arxiv.org/abs/1912.02175](https://arxiv.org/abs/1912.02175)
