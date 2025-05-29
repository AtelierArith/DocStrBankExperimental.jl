```
norm(g::HermLocalGenus) -> AbsSimpleNumFieldOrderFractionalIdeal
```

Return the norm of `g`, i.e. the norm of any of its representatives.

Given a local genus symbol `g` of hermitian lattices over $E/K$ at a prime ideal $\mathfrak p$ of $\mathcal O_K$, it norm is computed as the norm of the Jordan block of minimum $\mathfrak p$-valuation.
