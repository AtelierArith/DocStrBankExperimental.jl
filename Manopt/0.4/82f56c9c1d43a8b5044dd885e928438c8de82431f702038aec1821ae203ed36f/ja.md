```
ManifoldCostGradientObjective{T} <: AbstractManifoldObjective{T}
```

コストとその勾配の組み合わせ計算を行う関数を含む目的を指定します。

# フィールド

  * `costgrad!!`: コスト $f: \mathcal M → ℝ$ とその勾配 $\operatorname{grad}f: \mathcal M → \mathcal T\mathcal M$ の両方を計算する関数

[`AbstractEvaluationType`](@ref) `T` に応じて、勾配は2つの形式を持つことがあります。

  * メモリを割り当てる勾配 `X` のためにメモリを割り当てる関数 `(M, p) -> (c, X)`、[`AllocatingEvaluation`](@ref)
  * `X` のインプレースで動作する関数 `(M, X, p) -> (c, X)`、[`InplaceEvaluation`](@ref)

# コンストラクタ

```
ManifoldCostGradientObjective(costgrad; evaluation=AllocatingEvaluation())
```

# 使用例

[`gradient_descent`](@ref)、[`conjugate_gradient_descent`](@ref)、[`quasi_Newton`](@ref)
