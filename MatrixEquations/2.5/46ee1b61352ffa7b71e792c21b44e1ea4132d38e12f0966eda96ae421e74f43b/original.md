```
U = plyaps(A, B; disc = false)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the continuous Lyapunov equation

```
  AX + XA' + BB' = 0,
```

where `A` is a square real or complex matrix in a real or complex Schur form, respectively, and `B` is a matrix with the same number of rows as `A`. `A` must have only eigenvalues with negative real parts. Only the upper Hessenberg part of `A` is referenced.

```
U = plyaps(A', B', disc = false)
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the continuous Lyapunov equation

```
  A'X + XA + B'B = 0,
```

where `A` is a square real or complex matrix in a real or complex Schur form, respectively, and `B` is a matrix with the same number of columns as `A`. `A` must have only eigenvalues with negative real parts. Only the upper Hessenberg part of `A` is referenced.

```
U = plyaps(A, B, disc = true)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the discrete Lyapunov equation

```
  AXA' - X + BB' = 0,
```

where `A` is a square real or complex matrix in a real or complex Schur form, respectively, and `B` is a matrix with the same number of rows as `A`. `A` must have only eigenvalues with moduli less than one. Only the upper Hessenberg part of `A` is referenced.

```
U = plyaps(A', B', disc = true)
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the discrete Lyapunov equation

```
  A'XA - X + B'B = 0,
```

where `A` is a square real or complex matrix in a real or complex Schur form, respectively, and `B` is a matrix with the same number of columns as `A`. `A` must have only eigenvalues with moduli less than one. Only the upper Hessenberg part of `A` is referenced.
