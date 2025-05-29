```
prime_ideals_over(O::AbsSimpleNumFieldOrder,
                   lp::AbstractVector{Int};
                   degree_limit::Int = 0) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

Computes the prime ideals $\mathcal O$ over prime numbers in $lp$.

If `degree_limit` is a nonzero integer $k$, then prime ideals $\mathfrak p$ with $\deg(\mathfrak p) > k$ will be discarded.
