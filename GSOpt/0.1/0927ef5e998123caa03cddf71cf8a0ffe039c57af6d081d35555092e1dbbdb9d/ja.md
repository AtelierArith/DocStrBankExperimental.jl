```
JuMP.set_objective(model::GPModel, sense::MOI.OptimizationSense, func::AbstractGPExpression)
```

幾何プログラミングモデルの目的関数を設定します。

# 引数

  * `model::GPModel`: 幾何プログラミングモデル
  * `sense::MOI.OptimizationSense`: 最適化の感覚 (MIN*SENSE または MAX*SENSE)
  * `func::AbstractGPExpression`: 目的関数 (最小化の場合はポリソニアル、最大化の場合はモノミアルでなければなりません)

# 例外

  * 目的関数が最適化の感覚と互換性がない場合はエラーが発生します。
