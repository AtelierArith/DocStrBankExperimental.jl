```
polar(state::GaussianUnitary) -> Polar
```

Compute the Polar decomposition of the `symplectic` field of a `GaussianUnitary` object and return a `Polar` object.

`O` and `P` can be obtained from the factorization `F` via `F.O` and `F.P`, such that `S = O * P`. For the symplectic polar decomposition case, `O` is an orthogonal symplectic matrix and `P` is a positive-definite symmetric symplectic matrix.

Iterating the decomposition produces the components `O` and `P`.
