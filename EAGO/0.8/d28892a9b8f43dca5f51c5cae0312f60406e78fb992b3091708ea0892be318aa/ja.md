```julia
mutable struct SubSolvers{Q<:MathOptInterface.AbstractOptimizer, S<:MathOptInterface.AbstractOptimizer, T<:EAGO.ExtensionType}
```

緩和された最適化手法と上限最適化手法、およびユーザー定義の拡張を含む構造体です。

  * `relaxed_optimizer::MathOptInterface.AbstractOptimizer`: 緩和されたサブプロブレムを解くために使用される最適化手法。`r = [...]`を使用して設定します（<: `MOI.AbstractOptimizer`）         （デフォルト = `Cbc.Optimizer()`)
  * `upper_optimizer::MathOptInterface.AbstractOptimizer`: 上限問題を解くために使用される最適化手法。`u = [...]`を使用して設定します（<: `MOI.AbstractOptimizer`）         （デフォルト = `Ipopt.Optimizer()`)
  * `ext::EAGO.ExtensionType`: 使用するユーザー定義の拡張。`t = [...]`を使用して設定します（<: `EAGO.ExtensionType`）
