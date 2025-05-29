```
LeastSquaresLPResult{TF<:AbstractFloat} <: AbstractEstimatorResult
```

最小二乗ローカルプロジェクションの推定からの追加結果。 [`LeastSquaresLP`](@ref) および [`LocalProjectionResult`](@ref) も参照してください。

# フィールド

  * `ms::Vector{OLS{TF}}`: OLS回帰からのデータ。
