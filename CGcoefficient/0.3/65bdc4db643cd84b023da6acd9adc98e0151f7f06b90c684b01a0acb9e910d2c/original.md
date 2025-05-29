```
function unsafe_fbinomial(n::Int, k::Int)
```

Same as fbinomial, but without bounds check. Thus for `n < 0` or `n > _nmax` or `k < 0` or `k > n`, the result is undefined. In Wigner symbol calculation, the mathematics guarantee that `unsafe_fbinomial(n, k)` is always safe.
