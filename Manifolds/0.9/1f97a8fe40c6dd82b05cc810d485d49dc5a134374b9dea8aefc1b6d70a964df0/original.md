```
project(M:GeneralizedStiefel, p, X)
```

Project `X` onto the tangent space of `p` to the [`GeneralizedStiefel`](@ref) manifold `M`. The formula reads

$$
\operatorname{proj}_{\operatorname{St}(n,k)}(p,X) = X - p\operatorname{Sym}(p^{\mathrm{H}}BX),
$$

where $\operatorname{Sym}(y)$ is the symmetrization of $y$, e.g. by $\operatorname{Sym}(y) = \frac{y^{\mathrm{H}}+y}{2}$.
