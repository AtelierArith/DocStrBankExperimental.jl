```
exp(G::AbstractLieGroup, g, X)
exp!(G::AbstractLieGroup, h, g, X)
```

$$
g∈\mathcal G
$$

および $X∈\mathfrak g$ に対するリー群指数写像を計算します。ここで、$\mathfrak g$ は $\mathcal G$ の [`LieAlgebra`](@ref) を示します。これは次のように与えられます。

$$
\exp_g X = g∘\exp_{\mathcal G}(X)
$$

ここで `X` は `t` でスケーリング可能で、計算は `h` のインプレースで行うことができ、$\exp_{\mathcal G}$ は [Lie group exponential function](@ref exp(::AbstractLieGroup, ::Identity, :Any)) を示します。

もし `g` が [`Identity`](@ref) の場合、[Lie group exponential function](@ref exp(::AbstractLieGroup, ::Identity, :Any)) $\exp_{\mathcal G}$ は直接計算されます。リー群指数関数を実装することは、上記の式を用いたデフォルトの実装を導入します。

!!! note
    リー群指数写像は、通常、基礎となるリーマン多様体 $\mathcal M$ のメトリックに関する指数写像とは異なります。(リーマン)指数写像にアクセスするには、`exp(`[`base_manifold`](@ref)`(G), g, X)` を使用してください。


```
