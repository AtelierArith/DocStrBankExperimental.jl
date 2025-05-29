```
ManifoldGradientObjective{T<:AbstractEvaluationType} <: AbstractManifoldGradientObjective{T}
```

コストとその勾配を含む目的を指定します

# フィールド

  * `cost`:       関数 $f: \mathcal M → ℝ$
  * `gradient!!`: コスト関数 $f$ の勾配 $\operatorname{grad}f: \mathcal M → \mathcal T\mathcal M$。

[`AbstractEvaluationType`](@ref) `T` に応じて、勾配は2つの形式を持つことがあります

  * メモリを割り当てる関数 `(M, p) -> X`、[`AllocatingEvaluation`](@ref)
  * `X` の場所で動作する関数 `(M, X, p) -> X`、[`InplaceEvaluation`](@ref)

# コンストラクタ

```
ManifoldGradientObjective(cost, gradient; evaluation=AllocatingEvaluation())
```

# 使用例

[`gradient_descent`](@ref)、[`conjugate_gradient_descent`](@ref)、[`quasi_Newton`](@ref)
