```
exp(M::SymmetricPositiveSemidefiniteFixedRank, q, Y)
```

Compute the exponential map on the [`SymmetricPositiveSemidefiniteFixedRank`](@ref), which just reads

$$
    \exp_q Y = q+Y.
$$

!!! note
    Since the manifold is represented in the embedding and is a quotient manifold, the exponential and logarithmic map are a bijection only with respect to the equivalence classes. Computing

    $$
        q_2 = \exp_p(\log_pq)
    $$

    might yield a matrix $q_2\neq q$, but they represent the same point on the quotient manifold, i.e. $d_{\operatorname{SPS}_k(n)}(q_2,q) = 0$.

