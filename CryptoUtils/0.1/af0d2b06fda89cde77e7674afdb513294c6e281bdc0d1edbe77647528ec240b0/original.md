```
wiener(n::Integer, e::Integer, dujella_bound=20)
```

Factors the semiprime `n`, assuming Wiener's attack holds: `d < n^(1/4)`, where `d*e = 1 mod phi(n)`.

Uses Dujella extension attack. Increasing the `dujella_bound` argument slows the running time but increases chances of finding the correct `d` in case `d ~ n^(1/4)`.
