```
dets(g::HermLocalGenus) -> Vector{Int}
```

Given a local genus symbol `g` for hermitian lattices over $E/K$, return the determinants of the Jordan blocks of `g`.

The returned values are $1$ or $-1$ depending on whether the respective determinants are are local norms in `K`.
