```
convex_bundle_method!(M, f, ∂f, p)
```

`p`の代わりにバンドル法$p_{j+1} = \mathrm{retr}(p_k, -g_k)$を実行します。

# 入力

  * `M`:  多様体 $\mathcal M$
  * `f`:  最小化するコスト関数 $f:\mathcal M→ℝ$
  * `∂f`: Fの（部分）勾配 $∂f:\mathcal M→ T\mathcal M$。常に部分微分から1つの値/要素のみを返すように制限されています。この関数は、割り当て関数 `(M, p) -> X` または変異関数 `(M, X, p) -> X` として渡すことができます。詳細は `evaluation` を参照してください。
  * `p`:  初期値 $p_0=p ∈ \mathcal M$

詳細およびすべてのオプションのパラメータについては、[`convex_bundle_method`](@ref)を参照してください。
