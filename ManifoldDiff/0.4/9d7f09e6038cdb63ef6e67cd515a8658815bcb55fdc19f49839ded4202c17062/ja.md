```
riemannian_gradient(M, p, Y; embedding_metric=EuclideanMetric())
riemannian_gradient!(M, X, p, Y; embedding_metric=EuclideanMetric())
```

与えられた勾配 $Y = \operatorname{grad} \tilde f(p)$ が多様体の埋め込みにおいて、この関数は多様体 $M$ に制限された関数 $\tilde f$ のリーマン勾配 $\operatorname{grad} f(p)$ を計算します。これは `X` の代わりにインプレースで行うこともできます。

デフォルトでは、次の計算を使用します：$Y$ の $p$ における接空間への射影 $Z = \operatorname{proj}_{T_p\mathcal M}(Y)$ が与えられ、すなわち埋め込みにおける内積に関してです。すると

$$
⟨Z-Y, W⟩ = 0 \text{ for all } W \in T_p\mathcal M,
$$

または再配置すると $⟨Y,W⟩ = ⟨Z,W⟩$ となります。次にリーマン勾配の定義を使用します。

$$
⟨\operatorname{grad} f(p), W⟩_p = Df(p)[X] = ⟨\operatorname{grad}f(p), W⟩ = ⟨\operatorname{proj}_{T_p\mathcal M}(\operatorname{grad}f(p)),W⟩
\quad\text{for all } W \in T_p\mathcal M.
$$

最初の項と最後の項を比較すると、残りの計算は関数 [`change_representer`](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/metric.html#Manifolds.change_metric-Tuple{AbstractManifold,%20AbstractMetric,%20Any,%20Any}) です。

このメソッドは、より効率的/安定なバージョンが知られている場合、直接実装することもできます。

この関数は、[MatlabパッケージManopt](https://manopt.org) の `egrad2rgrad` に触発されています。
