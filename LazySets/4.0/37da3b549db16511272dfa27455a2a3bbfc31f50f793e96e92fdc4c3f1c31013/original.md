# Extended help

```
norm(H::AbstractHyperrectangle, [p]::Real=Inf)
```

### Algorithm

Recall that the norm is defined as

$$
‖ X ‖ = \max_{x ∈ X} ‖ x ‖_p = max_{x ∈ \text{vertices}(X)} ‖ x ‖_p.
$$

The last equality holds because the optimum of a convex function over a polytope is attained at one of its vertices.

This implementation uses the fact that the maximum is attained in the vertex $c + \text{diag}(\text{sign}(c)) r$ for any $p$-norm. Hence it suffices to take the $p$-norm of this particular vertex. This statement is proved below. Note that, in particular, there is no need to compute the $p$-norm for *each* vertex, which can be very expensive.

If $X$ is a hyperrectangle and the $n$-dimensional vectors center and radius of the hyperrectangle are denoted $c$ and $r$ respectively, then reasoning on the $2^n$ vertices we have that:

$$
\max_{x ∈ \text{vertices}(X)} ‖ x ‖_p = \max_{α_1, …, α_n ∈ \{-1, 1\}} (|c_1 + α_1 r_1|^p + ... + |c_n + α_n r_n|^p)^{1/p}.
$$

The function $x ↦ x^p$, $p > 0$, is monotonically increasing and thus the maximum of each term $|c_i + α_i r_i|^p$ is given by $|c_i + \text{sign}(c_i) r_i|^p$ for each $i$. Hence, $x^* := \text{argmax}_{x ∈ X} ‖ x ‖_p$ is the vertex $c + \text{diag}(\text{sign}(c)) r$.
