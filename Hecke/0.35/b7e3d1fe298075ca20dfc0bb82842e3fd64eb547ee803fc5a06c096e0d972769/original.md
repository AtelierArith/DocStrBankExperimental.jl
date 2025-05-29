```
prime_ideals_up_to(O::AbsSimpleNumFieldOrder,
                   B::Int;
                   degree_limit::Int = 0, index_divisors::Bool = true) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

Computes the prime ideals $\mathcal O$ with norm up to $B$.

If `degree_limit` is a nonzero integer $k$, then prime ideals $\mathfrak p$ with $\deg(\mathfrak p) > k$ will be discarded. If 'index_divisors' is set to false, only primes not dividing the index of the order will be computed.
