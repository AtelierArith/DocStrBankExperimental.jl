```
binomial(n::ZZRingElem, k::ZZRingElem)
```

Return the binomial coefficient $\frac{n (n-1) \cdots (n-k+1)}{k!}$. If $k < 0$ we return $0$, and the identity `binomial(n, k) == binomial(n - 1, k - 1) + binomial(n - 1, k)` always holds for integers `n` and `k`.
