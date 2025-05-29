```
det(g::HermLocalGenus) -> Int
```

Given a local genus symbol `g` for hermitian lattices over $E/K$ at a prime ideal $\mathfrak p$ of $\mathcal O_K$, return the determinant of a hermitian lattice whose $\mathfrak p$-adic completion has local genus symbol `g`.

The returned value is $1$ or $-1$ depending on whether the determinant is a local norm in `K`.
