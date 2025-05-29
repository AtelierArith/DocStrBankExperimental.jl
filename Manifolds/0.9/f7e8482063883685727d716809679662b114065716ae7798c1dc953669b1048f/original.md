```
project(M::Stiefel, p, X)
```

Project `X` onto the tangent space of `p` to the [`Stiefel`](@ref) manifold `M`. The formula reads

$$
\operatorname{proj}_{T_p\mathcal M}(X) = X - p \operatorname{Sym}(p^{\mathrm{H}}X),
$$

where $\operatorname{Sym}(q)$ is the symmetrization of $q$, e.g. by $\operatorname{Sym}(q) = \frac{q^{\mathrm{H}}+q}{2}$.
