```
ManifoldHessianObjective{T<:AbstractEvaluationType,C,G,H,Pre} <: AbstractManifoldHessianObjective{T,C,G,H}
```

ヘッセ行列に基づくアルゴリズムのための問題を指定します。

# フィールド

  * `cost`:           最小化する関数 $f:\mathcal M→ℝ$
  * `gradient`:       コスト関数 $f$ の勾配 $\operatorname{grad}f:\mathcal M → \mathcal T\mathcal M$
  * `hessian`:        コスト関数 $f$ のヘッセ行列 $\operatorname{Hess}f(x)[⋅]: \mathcal T_{x} \mathcal M → \mathcal T_{x} \mathcal M$
  * `preconditioner`: ヘッセ行列の逆の近似としての対称正定値前処理器で、コスト関数 $f$ のヘッセ行列が条件不良な場合に数値的に反復を安定させるために `hessian` と同じ入力変数を持つマップ

[`AbstractEvaluationType`](@ref) `T` に応じて、勾配は次の2つの形式を持つことがあります。

  * 関数 `(M, p) -> X` および `(M, p, X) -> Y`、それぞれ [`AllocatingEvaluation`](@ref)
  * 関数 `(M, X, p) -> X` および (M, Y, p, X)、それぞれ [`InplaceEvaluation`](@ref)

# コンストラクタ

```
ManifoldHessianObjective(f, grad_f, Hess_f, preconditioner = (M, p, X) -> X;
    evaluation=AllocatingEvaluation())
```

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
