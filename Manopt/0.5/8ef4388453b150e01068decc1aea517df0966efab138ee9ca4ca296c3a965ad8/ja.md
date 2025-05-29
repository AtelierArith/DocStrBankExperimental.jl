```
X = get_grad_inequality_constraint(M::AbstractManifold, emo::EmbeddedManifoldObjective, p, j)
get_grad_inequality_constraint!(M::AbstractManifold, X, emo::EmbeddedManifoldObjective, p, j)
```

埋め込みで定義された `j` 番目の不等式制約の勾配 $\operatorname{grad} g_j(p)$ を評価します。これは、勾配関数を呼び出す前に `p` を埋め込むことを意味し、[`EmbeddedManifoldObjective`](@ref) に格納されています。

返された勾配は、[`riemannian_gradient`](https://juliamanifolds.github.io/ManifoldDiff.jl/stable/library.html#ManifoldDiff.riemannian_gradient-Tuple{AbstractManifold,%20Any,%20Any}) を呼び出すことでリーマン勾配に変換されます。
