```
get_hessian(M::AbstractManifold, emo::EmbeddedManifoldObjective, p, X)
get_hessian!(M::AbstractManifold, Y, emo::EmbeddedManifoldObjective, p, X)
```

埋め込みで定義された目的のヘッセ行列を評価します。つまり、ヘッセ行列関数を呼び出す前に `p` と `X` を埋め込みます。この関数は [`EmbeddedManifoldObjective`](@ref) に格納されています。

返されたヘッセ行列は、[`riemannian_Hessian`](https://juliamanifolds.github.io/ManifoldDiff.jl/stable/library/#ManifoldDiff.riemannian_Hessian-Tuple{AbstractManifold,%20Any,%20Any,%20Any,%20Any}) を呼び出すことでリーマンヘッセ行列に変換されます。
