```
trust_regions!(M, f, grad_f, Hess_f, p; kwargs...)
trust_regions!(M, f, grad_f, p; kwargs...)
```

`p`の代わりにリーマン信頼領域ソルバーを評価します。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化するコスト関数 $f: \mathcal M → ℝ$
  * `grad_f`: 関数 $F$ の勾配 $\operatorname{grad}f: \mathcal M → T \mathcal M$
  * `Hess_f`: （オプション）ヘッセ行列 $\operatorname{Hess} f$
  * `p`:      初期値 $p  ∈  \mathcal M$

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細については、[`ApproxHessianFiniteDifference`](@ref)を参照してください。

詳細およびすべてのオプションについては、[`trust_regions`](@ref)を参照してください。
