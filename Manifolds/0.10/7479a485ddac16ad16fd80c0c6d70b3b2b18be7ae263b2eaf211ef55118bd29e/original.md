```
inner(M::ProbabilitySimplex, p, X, Y)
```

Compute the inner product of two tangent vectors `X`, `Y` from the tangent space $T_pΔ^n$ at `p`. The formula reads

$$
g_p(X,Y) = \sum_{i=1}^{n+1}\frac{X_iY_i}{p_i}
$$

When `M` includes boundary, we can just skip coordinates where $p_i$ is equal to 0, see Proposition 2.1 in [AyJostLeSchwachhoefer:2017](@cite).
