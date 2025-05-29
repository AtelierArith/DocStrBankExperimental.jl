```
prime_decomposition(O::AbsNumFieldOrder,
                    p::Integer,
                    degree_limit::Int = 0,
                    lower_limit::Int = 0) -> Vector{Tuple{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}}
```

Returns an array of tuples $(\mathfrak p_i,e_i)$ such that $p \mathcal O$ is the product of the $\mathfrak p_i^{e_i}$ and $\mathfrak p_i \neq \mathfrak p_j$ for $i \neq j$.

If `degree_limit` is a nonzero integer $k > 0$, then only those prime ideals $\mathfrak p$ with $\deg(\mathfrak p) \leq k$ will be returned. Similarly if `lower_limit` is a nonzero integer $l > 0$, then only those prime ideals $\mathfrak p$ with $l \leq \deg(\mathfrak p)$ will be returned. Note that in this case it may happen that $p\mathcal O$ is not the product of the $\mathfrak p_i^{e_i}$.
