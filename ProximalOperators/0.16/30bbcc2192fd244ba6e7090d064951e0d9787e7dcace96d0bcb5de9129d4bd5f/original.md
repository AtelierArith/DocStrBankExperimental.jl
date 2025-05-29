```
IndGraph(A)
```

For matrix `A` (dense or sparse) return the indicator function of its graph:

$$
G_A = \{(x, y) : Ax = y\}.
$$

The evaluation of `prox!` uses direct methods based on LDLt (LL for dense cases) matrix factorization and backsolve.

The `prox!` method operates on pairs `(x, y)` as input/output. So if `f = IndGraph(A)` is the indicator of the graph $G_A$, while `(x, y)` and `(c, d)` are pairs of vectors of the same sizes, then

```
prox!((c, d), f, (x, y))
```

writes to `(c, d)` the projection onto $G_A$ of `(x, y)`.
