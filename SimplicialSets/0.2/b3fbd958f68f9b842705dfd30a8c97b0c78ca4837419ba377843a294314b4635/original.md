```
IntervalSimplex <: AbstractSimplex

IntervalSimplex(p::Int, q::Int)
IntervalSimplex()
```

A type representing simplices in a simplicial interval (a 1-simplex). An `n`-simplex in a simplicial interval is determined by two non-negative integers `p` and `q` such that `p+q-1` equals `n`.

The first constructor above returns the `p+q-1`-simplex with `p` vertices equal to `0` and `q` vertices equal to `1`. The second constructor is a short form for `SimplicialInterval(1, 1)` and returns the unique non-degenerate `1`-simplex.
