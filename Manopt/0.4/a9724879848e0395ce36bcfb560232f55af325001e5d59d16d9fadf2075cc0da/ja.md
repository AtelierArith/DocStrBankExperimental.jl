```
adaptive_regularization_with_cubics!(M, f, grad_f, Hess_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, f, grad_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, mho, p; kwargs...)
```

`p`の代わりにリーマン適応正則化キュービックソルバーを評価します。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化するコスト関数 $F: \mathcal M → ℝ$
  * `grad_f`: $F$ の勾配 $\operatorname{grad}F: \mathcal M → T \mathcal M$
  * `Hess_f`: （オプション）$F$ のヘッセ行列 $H( \mathcal M, x, ξ)$
  * `p`:      初期値 $p  ∈  \mathcal M$

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細は [`ApproxHessianFiniteDifference`](@ref) を参照してください。

コスト `f` とその勾配およびヘッセ行列は、[`ManifoldHessianObjective`](@ref) として提供されることもあります。

詳細およびすべてのオプションについては、[`adaptive_regularization_with_cubics`](@ref) を参照してください。
