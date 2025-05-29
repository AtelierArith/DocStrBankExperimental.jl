```
subgradient_method!(M, f, ∂f, p)
subgradient_method!(M, sgo, p)
```

サブグラディエント法を実行します $p_{k+1} = \mathrm{retr}(p_k, s_k∂f(p_k))$、

# 入力

  * `M`:  多様体 $\mathcal M$
  * `f`:  最小化するコスト関数 $f:\mathcal M→ℝ$
  * `∂f`: Fの（サブ）勾配 $∂f: \mathcal M→ T\mathcal M$ は常にサブ微分から1つの値/要素のみを返すように制限されています。この関数は、割り当て関数 `(M, p) -> X` または変異関数 `(M, X, p) -> X` として渡すことができます。詳細は `evaluation` を参照してください。
  * `p`:  初期値 $p_0=p ∈ \mathcal M$

`f` と `∂f` の代わりに [`ManifoldSubgradientObjective`](@ref) `sgo` を提供することができます。

詳細およびすべてのオプションのパラメータについては、[`subgradient_method`](@ref) を参照してください。
