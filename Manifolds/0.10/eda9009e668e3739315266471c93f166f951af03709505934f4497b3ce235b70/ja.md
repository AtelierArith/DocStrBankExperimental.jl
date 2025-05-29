```
exp(::TraitList{IsConnectionManifold}, M::AbstractDecoratorManifold, p, X)
```

対応するアフィン接続を備えた [`IsConnectionManifold`](@ref) `M` 上の指数写像を計算します。

`M` が [`MetricManifold`](@ref) であり、[`IsDefaultMetric`](@ref) 特性を持つ場合、このメソッドは `exp(M, p, X)` にフォールバックします。

そうでない場合、基礎となる ODE を数値的に統合します。詳細は [`solve_exp_ode`](@ref) を参照してください。現在、数値的統合は、全体の多様体をカバーする単一の座標チャートを使用する場合にのみ正確です。これにより、埋め込まれた空間の座標は除外されます。
