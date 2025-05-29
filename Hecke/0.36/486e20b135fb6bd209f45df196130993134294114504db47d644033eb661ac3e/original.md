```
AbstractSpaceRes
```

A container type for map of change of scalars between vector spaces $V$ and $W$, each equipped with a non-degenerate sesquilinear form, where $V$ is a $K$-vector space for some number field $K$ and $W$ is a $E$-vector space for some finite simple extension `$E/K$.

Note: currently, only the case $K = \mathbb{Q}$ and $E$ a number field is available.

The underlying map `f` is actually considered as a map from $V$ to $W$. So in particular, $f(v)$ for some $v \in V$ is used to extend the scalars from $K$ to $E$, while the preimage $f\(w)$ for $w \in W$ is used to restrict scalars from $E$ to $K$.

Let $(a_1, \ldots, a_n)\in E^n$ be a $K$-basis of $E$, $B_V = (v_1, \ldots, v_l)$ be a $K$-basis of $V$ and $B_W = (w_1, \ldots, w_m)$ be an $E$-basis of $W$ where $l = m\times n$. Then, the map `f` defines a $K$-linear bijection from $V$ to $W$ by sending the $K$-basis $(v_1, \ldots, v_l)$ of $V$ to the $K$-basis $(a_1w_1, a_2w_1, \ldots, a_nw_1, a_1w_2, \ldots, a_nw_m)$ of $W$.

One can choose the different bases $B_V$ and $B_W$. However, for now, the basis of $E$ over $K = \mathbb{Q}$ is fixed by [`absolute_basis`](@ref).

By default, $B_V$ is the standard $K$-basis of $V$ and $B_W$ is the standard $E$-basis of $W$
