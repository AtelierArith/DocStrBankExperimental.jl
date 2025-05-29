```
prime_ideals_up_to(O::AbsSimpleNumFieldOrder,
                   B::Int;
                   complete::Bool = false,
                   degree_limit::Int = 0,
                   F::Function,
                   bad::ZZRingElem)
```

Computes the prime ideals $\mathcal O$ with norm up to $B$.

If `degree_limit` is a nonzero integer $k$, then prime ideals $\mathfrak p$ with $\deg(\mathfrak p) > k$ will be discarded.

The function $F$ must be a function on prime numbers not dividing `bad` such that $F(p) = \deg(\mathfrak p)$ for all prime ideals $\mathfrak p$ lying above $p$.
