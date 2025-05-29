```
factor(A::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}
```

Computes the prime ideal factorization $A$ as a dictionary, the keys being the prime ideal divisors: If `lp = factor_dict(A)`, then `keys(lp)` are the prime ideal divisors of $A$ and `lp[P]` is the $P$-adic valuation of $A$ for all $P$ in `keys(lp)`.
