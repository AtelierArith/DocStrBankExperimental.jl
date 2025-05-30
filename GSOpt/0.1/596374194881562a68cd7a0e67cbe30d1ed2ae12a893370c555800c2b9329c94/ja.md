```
JuMP.set_objective(model::SPModel, sense::MOI.OptimizationSense, func::AbstractGPExpression)
```

符号プログラミングモデルの目的関数を設定します。

# 引数

  * `model::SPModel`: 符号プログラミングモデル
  * `sense::MOI.OptimizationSense`: 最適化の感覚 (MIN*SENSE または MAX*SENSE)
  * `func::AbstractGPExpression`: 目的関数 (最小化の場合は符号項、最大化の場合は単項でなければなりません)

# 例外

  * 最適化の感覚と互換性のない目的関数の場合はエラーが発生します。
