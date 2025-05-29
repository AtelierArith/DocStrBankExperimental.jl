```
alternating_gradient_descent!(M::ProductManifold, f, grad_f, p)
alternating_gradient_descent!(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
```

`p`の代わりに交互勾配降下法を実行します。

# 入力

  * `M`:      積多様体 $\mathcal M$
  * `f`:      目的関数（コスト）
  * `grad_f`: サブ勾配のベクトルを返すか、勾配のベクトルである勾配関数
  * `p`:      初期値 $p_0 ∈ \mathcal M$

`f`と`grad_f`を含む[`ManifoldAlternatingGradientObjective`](@ref) `ago`を渡すこともできます。

すべてのオプションのパラメータについては、[`alternating_gradient_descent`](@ref)を参照してください。
