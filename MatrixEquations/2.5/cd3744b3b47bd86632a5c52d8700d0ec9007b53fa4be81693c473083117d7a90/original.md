```
U = plyaps(A, E, B; disc = false)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the generalized continuous Lyapunov equation

```
  AXE' + EXA' + BB' = 0,
```

where `A` and `E` are square real or complex matrices with the pair `(A,E)` in a generalied real or complex Schur form, respectively,  and `B` is a matrix with the same number of rows as `A`. The pencil `A - λE` must have only eigenvalues with negative real parts.

```
U = plyaps(A', E', B', disc = false)
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the generalized continuous Lyapunov equation

```
  A'XE + E'XA + B'B = 0,
```

where `A` and `E` are square real or complex matrices with the pair `(A,E)` in a generalied real or complex Schur form, respectively,  and `B` is a matrix with the same number of columns as `A`. The pencil `A - λE` must have only eigenvalues with negative real parts.

```
U = plyaps(A, E, B, disc = true)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the generalized discrete Lyapunov equation

```
  AXA' - EXE' + BB' = 0,
```

where `A` and `E` are square real or complex matrices with the pair `(A,E)` in a generalied real or complex Schur form, respectively,  and `B` is a matrix with the same number of rows as `A`. The pencil `A - λE` must have only eigenvalues with moduli less than one.

```
U = plyaps(A', E', B', disc = true)
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the generalized discrete Lyapunov equation

```
  A'XA - E'XE + B'B = 0,
```

where `A` and `E` are square real or complex matrices with the pair `(A,E)` in a generalied real or complex Schur form, respectively,  and `B` is a matrix with the same number of columns as `A`. The pencil `A - λE` must have only eigenvalues with moduli less than one.
