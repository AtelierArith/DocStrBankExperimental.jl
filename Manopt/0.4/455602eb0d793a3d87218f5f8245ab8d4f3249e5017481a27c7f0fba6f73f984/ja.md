```
get_gradient(M::AbstractManifold, emo::EmbeddedManifoldObjective, p)
get_gradient!(M::AbstractManifold, X, emo::EmbeddedManifoldObjective, p)
```

埋め込みで定義された目的の勾配関数を評価します。つまり、勾配関数を呼び出す前に `p` を埋め込みます。返された勾配は、[`riemannian_gradient`](https://juliamanifolds.github.io/ManifoldDiff.jl/stable/library.html#ManifoldDiff.riemannian_gradient-Tuple{AbstractManifold,%20Any,%20Any}) を呼び出すことでリーマン勾配に変換されます。
