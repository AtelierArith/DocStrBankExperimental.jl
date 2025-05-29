```
truncated_conjugate_gradient_descent!(M, f, grad_f, Hess_f, p, X; kwargs...)
truncated_conjugate_gradient_descent!(M, f, grad_f, p, X; kwargs...)
```

信頼領域サブプロブレムを `X`（および `p`）の代わりに解きます。

# 入力

  * `M`:      マンフォールド $\mathcal M$
  * `f`:      最小化するコスト関数 $F: \mathcal M → ℝ$
  * `grad_f`: `f` の勾配 $\operatorname{grad}f: \mathcal M → T\mathcal M$
  * `Hess_f`: ヘッセ行列 $\operatorname{Hess}f(x): T_p\mathcal M → T_p\mathcal M$, $X ↦ \operatorname{Hess}f(p)[X]$
  * `p`:      マンフォールド上の点 $p ∈ \mathcal M$
  * `X`:      更新接線ベクトル $X ∈ T_x\mathcal M$

詳細およびすべてのオプション引数については、[`truncated_conjugate_gradient_descent`](@ref)を参照してください。
