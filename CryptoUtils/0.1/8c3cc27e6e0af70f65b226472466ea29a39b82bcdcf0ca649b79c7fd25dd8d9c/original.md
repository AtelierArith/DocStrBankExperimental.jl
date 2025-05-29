```
factor_with_ed(n::Integer, e::Integer, d::Integer) -> (Integer, Integer)
```

Factors `n = p*q` given `(e, d)` such that `e*d = 1 mod phi(n)` Stinson page 204 - algorithm 5.10
