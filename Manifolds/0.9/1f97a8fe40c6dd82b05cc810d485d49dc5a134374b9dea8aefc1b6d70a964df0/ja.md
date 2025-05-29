```
project(M:GeneralizedStiefel, p, X)
```

点 `X` を [`GeneralizedStiefel`](@ref) 多様体 `M` の点 `p` の接空間に射影します。式は次のようになります。

$$
\operatorname{proj}_{\operatorname{St}(n,k)}(p,X) = X - p\operatorname{Sym}(p^{\mathrm{H}}BX),
$$

ここで、$\operatorname{Sym}(y)$ は $y$ の対称化であり、例えば $\operatorname{Sym}(y) = \frac{y^{\mathrm{H}}+y}{2}$ です。
