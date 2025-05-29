```
series(f::Function, L::Vector{M}) -> Series{C,M}
```

Compute the generating series $\sum_{x^{α} \in L} f(α) z^α$ for a function  $f: \mathbb{N}^n \rightarrow C$ and a sequence L of monomials.
