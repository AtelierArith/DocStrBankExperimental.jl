```
det(g::HermLocalGenus, i::Int) -> Int
```

Given a local genus symbol `g` for hermitian lattices over $E/K$, return the determinant of the `i`th Jordan block of `g`.

The returned value is $1$ or $-1$ depending on whether the determinant is a local norm in `K`.
