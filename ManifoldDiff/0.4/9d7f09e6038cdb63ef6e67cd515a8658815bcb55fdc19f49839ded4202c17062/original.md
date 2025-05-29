```
riemannian_gradient(M, p, Y; embedding_metric=EuclideanMetric())
riemannian_gradient!(M, X, p, Y; embedding_metric=EuclideanMetric())
```

For a given gradient $Y = \operatorname{grad} \tilde f(p)$ in the embedding of a manifold, this function computes the Riemannian gradient $\operatorname{grad} f(p)$ of the function $\tilde f$ restricted to the manifold $M$. This can also be done in place of `X`.

By default it uses the following computation: Let the projection $Z = \operatorname{proj}_{T_p\mathcal M}(Y)$ of $Y$ onto the tangent space at $p$ be given, that is with respect to the inner product in the embedding. Then

$$
⟨Z-Y, W⟩ = 0 \text{ for all } W \in T_p\mathcal M,
$$

or rearranged $⟨Y,W⟩ = ⟨Z,W⟩$. We then use the definition of the Riemannian gradient

$$
⟨\operatorname{grad} f(p), W⟩_p = Df(p)[X] = ⟨\operatorname{grad}f(p), W⟩ = ⟨\operatorname{proj}_{T_p\mathcal M}(\operatorname{grad}f(p)),W⟩
\quad\text{for all } W \in T_p\mathcal M.
$$

Comparing the first and the last term, the remaining computation is the function [`change_representer`](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/metric.html#Manifolds.change_metric-Tuple{AbstractManifold,%20AbstractMetric,%20Any,%20Any}).

This method can also be implemented directly, if a more efficient/stable version is known.

The function is inspired by `egrad2rgrad` in the [Matlab package Manopt](https://manopt.org).
