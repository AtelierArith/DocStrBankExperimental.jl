```
project(M::Stiefel, p, X)
```

点 `X` を [`Stiefel`](@ref) 多様体 `M` の点 `p` の接空間に射影します。式は次のようになります。

$$
\operatorname{proj}_{T_p\mathcal M}(X) = X - p \operatorname{Sym}(p^{\mathrm{H}}X),
$$

ここで、$\operatorname{Sym}(q)$ は $q$ の対称化であり、例えば $\operatorname{Sym}(q) = \frac{q^{\mathrm{H}}+q}{2}$ です。
