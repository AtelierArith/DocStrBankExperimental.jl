```
truncate(p::TrigPoly, n::Integer)
```

Reduce the length of `p.ac` and `p.as` to `n` by deleting coefficients. `n` cannot be larger than `p.n`.
