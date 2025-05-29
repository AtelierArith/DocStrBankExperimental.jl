```
log(M::SymmetricPositiveSemidefiniteFixedRank, q, p)
```

Compute the logarithmic map on the [`SymmetricPositiveSemidefiniteFixedRank`](@ref) manifold by minimizing $\lVert p - qY\rVert$ with respect to $Y$.

!!! note
    Since the manifold is represented in the embedding and is a quotient manifold, the exponential and logarithmic map are a bijection only with respect to the equivalence classes. Computing

    $$
        q_2 = \exp_p(\log_pq)
    $$

    might yield a matrix $q_2≠q$, but they represent the same point on the quotient manifold, i.e. $d_{\operatorname{SPS}_k(n)}(q_2,q) = 0$.

