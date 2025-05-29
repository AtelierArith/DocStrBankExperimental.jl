```
PrimeIdealsSet(O::AbsSimpleNumFieldOrder, f, t; proof = false,
                               indexdivisors = true,
                               ramified = true,
                               degreebound = degree(O),
                               coprimeto = false)
```

Returns an iterable object $S$ representing the prime ideals $\mathfrak p$ of $\mathcal O$ with $f \leq \min(\mathfrak p) \leq t$.

The optional arguments can be used to exclude index divisors, ramified prime ideals and to include only prime ideals with degree less or equal than `degreebound` and which are coprime to `coprimeto`.

If $t=-1$, then the upper bound is infinite.

If `coprimeto` is supplied, it must be either an integer, an element of $\mathcal O$, or a non-zero ideal of $\mathcal O$.
